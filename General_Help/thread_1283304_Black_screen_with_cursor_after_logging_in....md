---
title: "Black screen with cursor after logging in..."
date: 2009-10-05
forum: General Help
---

### Post by a-web on 2009-10-05
I am a newbie Ubuntu user; have been running Ubuntu 9.04 on a Compaq Presario 2100 for a couple months now - with no problems.

I recently reset my computer and when I log on there is only a black screen and my cursor.  Any help would be greatly appreciated.  (Remember I am a newbie, help will have to be step-by-step.)  Thanks.
              --Aw

---

### Post by Portable_Jim on 2009-10-05
I am not really into this type of problem. Bump.

---

### Post by fooman on 2009-10-05
> **a-web said:**
> I am a newbie Ubuntu user; have been running Ubuntu 9.04 on a Compaq Presario 2100 for a couple months now - with no problems.

I recently reset my computer and when I log on there is only a black screen and my cursor.  Any help would be greatly appreciated.  (Remember I am a newbie, help will have to be step-by-step.)  Thanks.
              --Aw

when you boot the computer and see the grub menu....choose "recovery mode"

when you see the recovery menu options....choose the xfix option.

give it a minute to complete,  then choose "continue with normal boot"

see if that helps.

---

### Post by a-web on 2009-10-07
> **fooman said:**
> when you boot the computer and see the grub menu....choose "recovery mode"

when you see the recovery menu options....choose the xfix option.

give it a minute to complete,  then choose "continue with normal boot"

see if that helps.


I did this... no change.  Still a black screen with cursor and no more....

---

### Post by a-web on 2009-10-07
I also tried this:
[http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html](http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html)

But to no avail...


Any other thoughts??  I am hitting bottom here with my ability to use Ubuntu.

---

### Post by a-web on 2009-10-08
I saw advice on techsupportforum.com for a similar problem to type "startx" and see what error happens (if any).  Here is my output:


Fatal server error:
Server is already active for display 0
            If this server is no longer running, remove /tmp/.X0-lock
            and start again.

Please consult the The X.Org Foundation support
              at [http://wiki.x.org](http://wiki.x.org)
  for help.

  ddxSigGiveUp: Closing log


Any advice??

---

### Post by a-web on 2009-10-08
I FIXED IT!!!!

I am not sure this is it, but the last thing I did was (if anyone else has a similar problem):

1.  I went to a coffee shop with free and non-passworded wireless.
2.  Booted the computer into "recovery mode" and choose "netroot  Drop to *root* shell prompt  with networking".
3.  Entered the following
Code:
 	sudo apt-get update
sudo apt-get install ubuntu-desktop 
4.  Reboot.

And now I can see the desktop, use my computer and etc!!  (I am a proud newbie now.)

---

### Post by Portable_Jim on 2009-10-10
Now to mark the thread as solved. To do that, go up to the top of the thread, into "Thread Tools" and there should be something to let you indicate that the problem is solved.

---

