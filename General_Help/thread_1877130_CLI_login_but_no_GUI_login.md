---
title: "CLI login but no GUI login"
date: 2011-11-07
forum: General Help
---

### Post by jcllings on 2011-11-07
I think the display manager is lightdm. Tried removing ~/.ICEauthority as suggested in one posting. No dice. 

What happens is that I enter my userid and password and it just doesn't let me log in. Is there a log file somewhere that I could look at? Any other ideas?  I've not worked on this system in quite a while. Problem was occurring before I upgraded to latest Ubuntu (11.x).  At one point, was able to shut X down and use startx to get in. BTW, what is the means normally used on Ubuntu for shutting down X?  It kept restarting on me. 


Jim C.

---

### Post by jcllings on 2011-11-07
Well, by now I've tried quite a number of things and none of them have worked. I've created a new user and he had the same problems. Couldn't log in from GUI but CLI not a problem. Tried re-installing X server. I did figure out how to stop the display manager so I've been using startx. I've removed .Xauthority and .ICEauthority... getting towards the end of my rope here. What log files should I be looking at?


Jim C.

---

### Post by jcllings on 2011-11-07
Uh oh. I found it. The system hates my customized bash profile despite the fact that previous systems were fine with it. 


jim@midknight:~$ cat .xsession-errors 
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/jim/.profile
...then right here it was complaining about redirection

In particular, it was complaining about this line:

PATH=`awk -F: '{for(i=1;i<=NF;i++){if(!($i in a)){a[$i];printf s$i;s=":"}}}'<<<$PATH` #Eliminate duplicate path entries

What it does is eliminate duplicates from the command path. It hated the triple <<< for the 'here' document but this produces no errors or problems if you source it or use bash -x to process it. 

Could this be a bug? #1, the profile isn't bad but... #2. If it were bad, shouldn't X load anyway or at least raise a bigger fuss with a more plainly visible GUI error message?
 

Jim C.

---

### Post by dunbrokin on 2011-11-16
That did not work for me...still have a problem - see [http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---

