---
title: "Blank Screen after Login"
date: 2009-09-03
forum: General Help
---

### Post by Jazzy_Jeff on 2009-09-03
I am having a problem. I restarted this morning and after I log in all I get is a blank screen. All I can see is the mouse pointer. I logged into recovery mode and ran the tests and it shows everything is fine. I am running 9.04.

---

### Post by Jazzy_Jeff on 2009-09-03
I am still having a problem here. Can someone tell me how I can access my home partiton using puppy linux? I want to save a few files before I reinstall. 

When I go into my home folder it says Access-Your-Private-Data.desktop. How can I copy files from here to another hard drive?

---

### Post by jaxxstorm on 2009-09-03
> **Jazzy_Jeff said:**
> I am still having a problem here. Can someone tell me how I can access my home partiton using puppy linux? I want to save a few files before I reinstall. 

When I go into my home folder it says Access-Your-Private-Data.desktop. How can I copy files from here to another hard drive?

Is your home directory encrypted? Did you choose that option when you first installed Ubuntu?

If you didn't, have you mounted your hard drive? I'm not sure if Puppy does that automagically.

---

### Post by NinjaNumberNine on 2009-09-03
To fix the black screen go in tty when you system reaches the logon screen (ctrl-alt-f3, or any other f#from 2 to 7) and log in, then follow prompts to log in and then type "sudo apt-get remove compiz" and "sudo apt-get remove compiz-core" then reboot and try to login normally again and post any problems here. good luck!

---

### Post by FlyingBuzz on 2009-09-03
> **NinjaNumberNine said:**
> To fix the black screen go in tty when you system reaches the logon screen (ctrl-alt-f3, or any other f#from 2 to 7) and log in, then pollow prompts to log in and then type "sudo apt-get remove compiz" and "sudo apt-get remove compiz-core" then reboot and try to login normally again and post any problems here. good luck!
In addition I would say that I had a problem with desktop. It used to freeze every time I log in. So, i couldn't see icons, I couldn't click on it both wirh left and right mouse buttons. And the only way to overcome that was to run Alt+F2 and 'nautilus' there.

The soluton is easy.

If the problem is not in compiz try to remove your /home/username/.nautilus directory.

So go to Ctrl+Alt+ any of Fs from 1 to 6, log in and execute the following:

sudo rm -rf /home/<your username>/.nautilus

And then:

sudo reboot

Then try to do normal login as usual.
Removing .nautilus directory won't delete your own files or neccessary system files. It only forces the system to generate and load default settings for nautilus if (maybe) tne previous ones were incorrect.

---

### Post by Jazzy_Jeff on 2009-09-03
Thank you. I will try this. It can't be compiz because it is not running right now. I have it disabled.

---

### Post by Jazzy_Jeff on 2009-09-03
> **FlyingBuzz said:**
> In addition I would say that I had a problem with desktop. It used to freeze every time I log in. So, i couldn't see icons, I couldn't click on it both wirh left and right mouse buttons. And the only way to overcome that was to run Alt+F2 and 'nautilus' there.

The soluton is easy.

If the problem is not in compiz try to remove your /home/username/.nautilus directory.

So go to Ctrl+Alt+ any of Fs from 1 to 6, log in and execute the following:

sudo rm -rf /home/<your username>/.nautilus

And then:

sudo reboot

Then try to do normal login as usual.
Removing .nautilus directory won't delete your own files or neccessary system files. It only forces the system to generate and load default settings for nautilus if (maybe) tne previous ones were incorrect.

I tried this and it did not work. I think I may have found what the problem is.

A couple of days ago I changed my password. This morning was the first time I rebooted. It appears that my home directory is encrypted. I don't remember doing it, but I play with my system all the time :D. When I goto the command line and go into the ecrypts-private that pops up it wants my old pass phrase. 

How can I change my password back to the one I had before using the command line? I hope this will fix the problem.

---

### Post by NinjaNumberNine on 2009-09-03
> I tried this and it did not work. I think I may have found what the problem is.

A couple of days ago I changed my password. This morning was the first time I rebooted. It appears that my home directory is encrypted. I don't remember doing it, but I play with my system all the time :D. When I goto the command line and go into the ecrypts-private that pops up it wants my old pass phrase. 

How can I change my password back to the one I had before using the command line? I hope this will fix the problem. 	 No ideas how to do that from me, but that might be your problem, true. You never know in linux! :D But what do you mean by "I disabled compiz"?? I don't know how to say this, but did you navigate to desktop settings where you can change your wallpaper and go under the "effects" tab and click "none"?  Thats how I remember having to do it. Also, did you try the commands? It might be disabled but not removed. Anyway, these are just suggestions. I wish I could help you with the permissions thing, but I know less about it then you do probably! :D

---

### Post by Jazzy_Jeff on 2009-09-03
I figured out how to change my password via command line and guess what? I am in. So I guess I can't change my password without doing something with the encrypted home folder.

---

### Post by NinjaNumberNine on 2009-09-03
Thats great! I never knew permissions could keep you from seeing your desktop, except, like, maybe if you forgot your password and couldn't log in!!  :-\"
Anyway, glad you got it fixed!

---

