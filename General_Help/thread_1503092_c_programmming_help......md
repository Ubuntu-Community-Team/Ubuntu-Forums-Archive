---
title: "c programmming help....."
date: 2010-06-06
forum: General Help
---

### Post by amite on 2010-06-06
I don't know whether this ques. should be asked here or not......but i suppose i must get any solution so i am posting these question.

> 
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <signal.h>

main()
{
     if(fork()==0) //IF CHILD
     {
          char ch;
         while(1)
        {
             ch=rand();
             printf("%c ",ch);
        }
     }
    else   //PARENT PROCESS
    {
        if(getchar()==27)  //if 'esc' pressed send SIGKILL signal
            signal(SIGINT,SIG_DFL);
    }

}


I am learning c programming.My requirement is after executing this program terminal give random char to stdout and when i press esc then it stop.So i start a child to give output random characters and parent process wait for esc character.after pressing esc parent send kill -9 signal to terminate it self and so child also terminated.

Before using SIGKILL  i tried sigchld to terminate child and after that parent terminate normally.but both doesn't working,after executing the process i have to use ctrl+c to stop the process.

**I want to just know why is it not working,where  is wrong in my approach?**
if any one have also other approach to solve the sameproblem please suggest me....

Thanks ...:smile:

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
You might get more help in the [Programming]("http://ubuntuforums.org/forumdisplay.php?f=39") thread.

---

### Post by stderr on 2010-06-06
Well, it looks like you're connecting the Terminate signal to the close action (which I think should happen by default), but then not actually sending a terminate signal. IMHO, you want to grab the child PID from fork and stick it in a variable. Then, instead of signal(...) use a kill(child_pid, SIGINT)

---

### Post by happyhamster on 2010-06-06
Also, pressing ESC usually won't be enough: the input buffer has to be flushed for the character to be read (usually by pressing the enter key).

---

