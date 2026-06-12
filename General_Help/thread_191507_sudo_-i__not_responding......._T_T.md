---
title: "sudo -i  not responding....... T_T"
date: 2006-06-07
forum: General Help
---

### Post by James- on 2006-06-07
> 
james@LinuxServer:~$ sudo -i
james@LinuxServer:~$

I don't know why it wouldn't work it was working before....
It doesn't even want to let me use sudo.... I think I know why... I changed my user of groups to ftpusers.. I need to know how to set so that I can get sudo back :(

---

### Post by Ramses de Norre on 2006-06-07
Are you still in the admin group too? Can you use sudo without the -i option?

---

### Post by tonyr on 2006-06-07
If you used **useradd** to change your group to **ftpusers**, then that's exactly
what happened.

Here's a thread about how to recover (hmmm...**Ramses de Norre** is in there, too, so listen to what he says...)
[http://www.ubuntuforums.org/showthread.php?t=189132]("http://www.ubuntuforums.org/showthread.php?t=189132")

---

### Post by 5-HT on 2006-06-07
[LEFT]Your description doesn't really provide enough information for troubleshooting, but I believe you may have removed yourself from the admin/adm group that sudo is set up to give root permissions to.

If you enter ```
 groups 
``` Do you see admin/adm listed?
If not, the following should fix the problem.

You'll need to boot into recovery mode (press 'esc' at the grub screen during boot, select 'recovery mode' and press enter).[LIST=1]
[*]Once you get a prompt, you'll need to find out whether which group sudo is set up to give root permissions to (can be either 'adm or 'admin' depending on which version of Ubuntu you originally installed): ```
 cat /etc/sudoers 
``` Look at the last line of the file under ```
 # Members of the admin group may gain root privileges 
``` The line should start with either %admin or %adm[/LIST]Add yourself to the relevant group (either 'admin' or 'adm'): ```
 adduser your_username admin
``` OR ```
 adduser your_username adm 
``` 

That should hopefully fix the problem.

If you are a member of admin/adm and are still having issues, we can try other things.

Hope that helps.

EDIT: too slow, much better to link I guess

[/LEFT]

---

### Post by James- on 2006-06-07
[QUOTE=tonyr]If you used **useradd** to change your group to **ftpusers**, then that's exactly
what happened.

Here's a thread about how to recover (hmmm...**Ramses de Norre** is in there, too, so listen to what he says...)
[http://www.ubuntuforums.org/showthread.php?t=189132]("http://www.ubuntuforums.org/showthread.php?t=189132")[/QUOTE]
Yeah thats exactly what I did :(  now I don't have access tu bullcrap :/ 


P.s. I think it will fix my problem ^^ thank you for the fast reply!

---

