# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }

##OUTPUT



![317285810-97ef94a4-3c10-4fef-b437-a69ca986feda](https://github.com/gowriganeshns/Linux-Process-API-fork-wait-exec/assets/144870750/6519589d-f624-4a9e-b49d-d839135d1abb)



## C Program to create new process using Linux API system calls fork() and exit()



#include <stdio.h>
#include<stdlib.h>
int main()
{ 
int pid; 
pid=fork(); 
if(pid == 0) 
{ 
printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); 
} 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);
} 
}

##OUTPUT

![image](https://github.com/varshinidevaraju/Linux-Process-API-fork-wait-exec/assets/144870750/25934605-3051-4d61-a392-756d655e24fc)


## C Program to execute Linux system commands using Linux API system calls exec() family


#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{
        int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                printf("child did not exit successfully\n");
                printf("Done.\n");
                printf("Running ps with execlp. Now with path specified\n");
                execlp("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                printf("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);
}




##OUTPUT

https://private-user-images.githubusercontent.com/148959215/317284245-23d6b25d-b9f2-4c7d-b336-448ce857fb8e.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTM3MjA0MzAsIm5iZiI6MTcxMzcyMDEzMCwicGF0aCI6Ii8xNDg5NTkyMTUvMzE3Mjg0MjQ1LTIzZDZiMjVkLWI5ZjItNGM3ZC1iMzM2LTQ0OGNlODU3ZmI4ZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNDIxJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDQyMVQxNzIyMTBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02YWI0MzY2MDE2MDNhMTU4NjBmNzNjZjM0MmU1ZTM2MGI3ZGM4ZTNiMTM1ODg5ZjU2NTVjYWJmZGFiYzA3MTAzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.p2o0-00KB0MEKowYWWSUy1ExJG2OiZnAnFHsIsG6oA8



# RESULT:
The programs are executed successfully.
