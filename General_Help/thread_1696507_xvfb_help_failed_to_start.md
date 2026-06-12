---
title: "xvfb help failed to start"
date: 2011-02-27
forum: General Help
---

### Post by pseng on 2011-02-27
Hi, I am thrown in at the deep end and I am trying to get xvfb running but feel like I am doing a driving test blindfolded after a bottle of vodka when I go through the stuff google throws out when I search for help. I get the message when I try xvfb-run xvfb failed to start. I simply don't know where to start trouble shooting as I can't find or create an error log. I am using an aws systen and need it to keep running in the background so that I can use cutycapt, which is the main reason I have to work with it. I am on i386 with ubuntu maverick 10.10. I have installed the fonts and dependent software I think. I know that this is a tall order but any help would be greatly appreciated.

Thanks

---

### Post by cjhabs on 2011-02-27
Are you trying to start it with sudo? I think it would need to be.

---

### Post by pseng on 2011-02-27
Hi, yes I am using the using sudo account, although I will probably have to do chown for the service to run.

---

### Post by cjhabs on 2011-02-27
> **pseng said:**
> Hi, yes I am using the using sudo account, although I will probably have to do chown for the service to run.

After the Xvfb-run command exits, run:
echo $?
This will provide the exit status of the command.
Then look at the man page for Xvfb-run - it lists the exit status errors - this may help you narrow down the problem.

---

### Post by pseng on 2011-02-28
Thanks, that was helpful. I have the exit code 1

[FONT=Fixedsys]xvfb-run The command-line options could not be processed.
[/FONT]
also managed to generate the error.log

Fatal server error:

[FONT=Fixedsys]Server is already active for display 99
        If this server is no longer running, remove /tmp/.X99-lock
        and start again[/FONT].
[FONT=Verdana]have established that services running 

[FONT=Fixedsys]root@sys:/var/log# ps aux | grep `cat /tmp/.X2-lock`
root      4272  0.0  0.0   3700   752 pts/2    S+   11:58   0:00 grep --color=auto 20912
root     20912  0.0  0.3  12420  5932 ?        S    Feb27   0:00 Xvfb :2 -screen 0 640x480x8 -nolisten tcp
root@sys:/var/log# ps aux | grep `cat /tmp/.X1-lock`
root      4315  0.0  0.0   3700   756 pts/2    S+   11:58   0:00 grep --color=auto 20265
root     20265  0.0  0.4  14264  7744 ?        S    Feb27   0:00 Xvfb :1 -screen 0 800x600x24
root@sys:/var/log# ps aux | grep `cat /tmp/.X0-lock`
root      2692  0.0  0.4  13400  6920 ?        S    Feb27   0:00 /usr/bin/Xvfb
root      4334  0.0  0.0   3700   752 pts/2    S+   11:58   0:00 grep --color=auto 2692
root@sys:/var/log# ps aux | grep `cat /tmp/.X99-lock`
root      1634  0.0  0.1  13512  2612 ?        S    Feb25   0:00 Xvfb :99 -ac
root      4353  0.0  0.0   3700   752 pts/2    S+   11:58   0:00 grep --color=auto 1634

[FONT=Verdana]I also use x2go sometimes. 

Thanks
[/FONT][/FONT]

[/FONT]

---

### Post by cjhabs on 2011-02-28
So, I am not too clear on where you stand?
What arguments are you using to the command? Which server number are you trying to start?
Did you remove the temp files associated with that server number?
What error do you get when you try to render using that server?

---

### Post by pseng on 2011-03-03
Sorry I have not answered but baby things have taken up my time. Thank you for you help but I am trying to start it using the xvfb-run command. I am not entirely sure what arguments to use when I start it and have used the example code from the page.

[FONT="Fixedsys"]xvfb-run --auto-servernum --server-num=1 xlogo[/FONT]

 What exactly does it mean servernumber, listen and screen? What arguments should I be using?

Thanks

---

### Post by cjhabs on 2011-03-03
> **pseng said:**
> Sorry I have not answered but baby things have taken up my time. Thank you for you help but I am trying to start it using the xvfb-run command. I am not entirely sure what arguments to use when I start it and have used the example code from the page.

[FONT=Fixedsys]xvfb-run --auto-servernum --server-num=1 xlogo[/FONT]

 What exactly does it mean servernumber, listen and screen? What arguments should I be using?

Thanks

I am not familiar with xvfb-run as I use this on a Solaris box - but X uses screen numbers - 0 is usually the physical frame buffer - you can pick any number you want, but you need to make sure that you direct your display variable to that screen.

xterm -display xx.xx.xx.xx:3
will render on screen 3

I suspect you should not be using [FONT=Fixedsys] --auto-servernum  and --server-num=1[/FONT] together - I would just use the latter, where you can control the screen number yourself.

---

