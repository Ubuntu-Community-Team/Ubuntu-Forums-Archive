---
title: "WINE Workaround, is it safe?"
date: 2012-06-11
forum: General Help
---

### Post by doogie544 on 2012-06-11
To run certain Windows programs in WINE in 12.04 you need to this workaround:
  
```
echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
``` According to the support websites, this is due to a bug in the Ubuntu  kernel that prevents ptrace and WINE playing well together.
  Using the above command you set the ptrace to 0 which according the  research I've done(don't ask me which websites, I have seem a lot of  them), ptrace has to do with the interactions between programs.  The 0  setting is more permissive than the 1.  
  I have to assume that there was a good reason Ubuntu wanted the  ptrace=1 so this leads me back to the short form of the question.
  Are there any risks involved in setting ptrace=0.  Lower security? problems debugging?  any others that I haven't thought of???
  

P.S.  for anybody reading this that wonders what the bug causes, the  Windows programs will fail to open at all, in the System Monitor you  will see many instances of the program trying to open and then they will  eventually all quit and if you run the progam for the terminal you will  get an error that tells you that the maximum number of program  instances has been reached.

---

### Post by Toz on 2012-06-17
> I have to assume that there was a good reason Ubuntu wanted the ptrace=1 so this leads me back to the short form of the question.
Are there any risks involved in setting ptrace=0. Lower security? problems debugging? any others that I haven't thought of???Here is an explanation of what it is and what the consequences are: [https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection]("https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection"). I have ptrace set to 0 as I need it to establish an F5 vpn tunnel.

---

### Post by doogie544 on 2012-06-17
@Toz
Thank you for those links, I don't think I found those when I was searching.  I'm not sure why, if this has been around since Maverick.  WIne was working fine up until the release of 12.04 now there is some regression that was not caught in the evaluation cycle.  I would have thought that someone would have caught that one esp. with it being a LTS.](*,)

One more question I only need the ptrace=0 for Wine.  I have a text file saved as an executable so that I don't have to type it every time, but how would I go about changing it so that it will run without prompting for a password every time?  I don't want my daughter to call me in every time she wants to play a game but I sure as he!! don't want her to have my admin. password.

---

### Post by Toz on 2012-06-18
One way (not sure if its the best), is to change the permissions on the **/proc/sys/kernel/yama/ptrace_scope** file to be world-readable. You could do this by adding:
```
chmod 666 /proc/sys/kernel/yama/ptrace_scope
```
...to the end of **/etc/rc.local** before the *exit 0* command. This will change the permissions to that file on computer startup.

Then within your script, you should be able to:
```
echo 0 > /proc/sys/kernel/yama/ptrace_scope
```
...as a normal user and revert with a:
```
echo 1 > /proc/sys/kernel/yama/ptrace_scope
```

---

### Post by doogie544 on 2012-06-19
Thanks for the quick response but I think I phrased my  follow up question poorly

I know how to permanently change the ptrace, the method for only changing it at startup is new to me. The second question was a little more general I have an executable text file (in my home folder)that reads

    echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope

That is the whole file posted above, an exact copy and paste

As I only need to set the ptrace for a few programs, I would prefer to just set it when I need it so what I need to know is how to edit the above line to make it executable without having to enter my password every time I run the script.

I would prefer to keep the better security that ptrace offers and only open the gate(so to speak) when I need to run those finicky windows programs so that it will revert at the next login.

---

### Post by Toz on 2012-06-19
If I'm understanding correctly, I believe my previous answer will still work. The first command in /etc/rc.local will give all users of the computer write access to that file so sudo will _not_ be required and thus a password will not need to be entered.

Then, in the script that starts your wine program, do something like this:
```

#disable ptrace_scope protection
echo 0 > /proc/sys/kernel/yama/ptrace_scope 

# start wine program
<command to start wine program>

#re-enable ptrace_scope protection
echo 1 > /proc/sys/kernel/yama/ptrace_scope 

```

If you just want to change the ptrace script that you already have, change the command to:
```
echo 0 > /proc/sys/kernel/yama/ptrace_scope
```
...no sudo needed because you have given the user write permission to the /proc/sys/kernel/yama/ptrace_scope file.

---

### Post by izx on 2012-06-21
Guys, setting ptrace_scope world-writable is a VERY BAD IDEA, because now any process that wants to can modify it, making the protection useless!

Doing it program by program using the CAP_SYS_PTRACE capability on a per-file basis is a much better way. For Wine this would be the wineserver and wine-preloader binaries.

Please see [my answer]("http://askubuntu.com/a/153970/58612") to dougie544's AskUbuntu question for more information and details on how to set the ptrace capability.

---

### Post by Toz on 2012-06-21
Thanks for the explanation izx. I wasn't aware of the setcap functionality, but it makes more sense (and is more secure) than the world-readable solution.

---

