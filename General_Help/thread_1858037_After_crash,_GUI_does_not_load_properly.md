---
title: "After crash, GUI does not load properly"
date: 2011-10-11
forum: General Help
---

### Post by MutantJohn on 2011-10-11
Hello All,

So, I converted wholeheartedly to linux after my Windows 7 drive failed and I've been loving Ubuntu 11.04 ever since. Yesterday, I decided I couldn't wait and just had to upgrade to 11.10 so I settled with the beta 2. 11.10 beta 2 is actually pretty cool but now I have some problems.

The last thing I was doing before everything went to hell was that I had a chromium page open on GameFAQs, synaptic was open with the search for compiz in there and I was looking at the CompizConfig and trying to figure out how I can alt-tab out of Heroes of Newerth because the alt-tab feature wasn't working for it.

Well, what happened when I was doing this is, my computer screen just straight up froze completely. Completely unresponsive to anything (mouse clicks and my keyboard), I just hit the restart button on my computer case and when I restarted and attempted to use my 3.0.something linux kernel, my task bar completely vanished along with the stuff in the upper right hand corner that displays time, if you're connected to the internet and also gives you the ability to shut you computer down.

I have a grub screen from trying to install Windows 7 on a second hard drive so I tried running previous versions of the linux kernel (2.6.something or w/e 11.04 was) but my computer treats the previous kernel version as 11.10 so the same thing happens. It worked correctly the first time I tried but it wasn't detecting my graphics driver (I'm using nvidia) so when I changed it because my resolution is better thant 1200x800, I get the same thing. No task bar, no nothing. I have to use nothing but hotkeys and whatever I can run through the terminal.

So can someone please help me?

---

### Post by grahammechanical on 2011-10-11
First, it is my guess that the freeze you describe was due to running out of memory. I have experienced similar freezes on 11.10. I usually wait for the system to sort itself out. Stuff has to be paged out of Ram memory into swap (hard disk space) memory and back again as the OS completes the tasks that you have set it.

Second, from previous posts that I have seen I would say that you need to re-start Unity or possibly Compiz. Look for posts related to that subject. Look in the part of the forum set aside for Oneiric

[http://ubuntuforums.org/forumdisplay.php?f=403]("http://ubuntuforums.org/forumdisplay.php?f=403")

Regards.

---

### Post by TeoBigusGeekus on 2011-10-11
Open a terminal and give
```
unity --reset
```
to (attempt to) reset unity and then
```
sudo reboot
```
to... reboot.
Post us what happened.

---

### Post by lincoln32 on 2011-10-11
I had several failed Downloads but 11.10 is stable and working great on
the six I have tested it with. That said it is Beta new releases tend to buggy for a while I normally wait several months before recommending it be installed on anything other than a test box or virtualbox

---

### Post by oldos2er on 2011-10-11
Thread title changed to something more appropriate.

---

### Post by MutantJohn on 2011-10-11
Ha ha, I'm sorry mods. But yes, I did try the unity --reset command and this is the output that I received (spoilers, it didn't do anything):

unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done

---

### Post by erixnow on 2011-10-11
use a utility to check the checksum of the .iso image.  I have run into issues also due to the fact that the image was corrupted.  I was also looking to beta 11.  I have a server I wanted to load VMWare on so have to stick with supported LTS versions.


Have you found it to have alot of bugs ?

EDIT:
  what video card chipset is it.  can you post config?


Regards,
  Eric Peyser

---

### Post by MutantJohn on 2011-10-11
So the thing is, it's like the process doesn't even finish. Like, you know how it's supposed to say username@blahblahblah:~$? Well, it doesn't. So when I close the terminal it'll tell me a process is still running and a restart does nothing on top of that : P

I'm pretty sure I'm going to have to re-format my hard drive (i.e. erase everything on it) and do a clean install when the non-beta 2 is release in like two days. I guess this is what what I get for not being patient, ha ha. I'm not as mad as I was when the errors started occurring but I'm good enough with linux now to not absolutely NEED a GUI although I do consider having a GUI a symbol of better programming.

I already sent the help team a rather interesting email full of swears, nerd-rage and why I truly love them so we'll see what they have to say.

Thank you for all your help those that tried. And now I know to never ever ever ever ever use the upgrade button because the upgrade button is the mislabeled make everything go to **** button.

---

### Post by TeoBigusGeekus on 2011-10-11
> **MutantJohn said:**
> ...
unity-panel-service: no process found
...
What if you try to start the service?
```
unity-panel-service
```

---

### Post by MutantJohn on 2011-10-11
If I type in

```
unity-panel-service
```it tells me that the command is not found. Do I just use 

```
 sudo apt-get unity
```?

---

### Post by TeoBigusGeekus on 2011-10-11
Ok, ok, I guess your system is screwed up and since I know nadda about unity and prefer to keep it this way, the only thing I can offer you is to create another user:
```
sudo adduser
```
Follow the instructions and answer all the questions.

Next, add a password for this user
```
sudo passwd NewUserName
```

Replace NewUserName with the user name you gave while executing the adduser command.
Give your new password and then

```
sudo EDITOR=nano visudo
```

Add this line at the end of the file

```
NewUserName ALL=(ALL) ALL
```

NewUserName is your new user name.

ctrl+x to exit (answer yes to save the file)

and finally

```
sudo reboot
```

Log in with your new user name and post us what happened.

---

### Post by MutantJohn on 2011-10-11
You sir, are a genius. I am logged in now as MutantJohn on my computer and I finally have my GUI back. Now that is truly awesome. Thank you, thank you, thank you. I'll definitely come back in a heartbeat if this whole thing doesn't pan out though lol.

---

### Post by TeoBigusGeekus on 2011-10-11
Wait...
...some more things to do.
If you go to /home/YourOldUserName, you can find everything you had in your old home folder.
You can copy web browser folders, pictures, videos, favourite programs' settings, etc.
After you're done, you can delete the old user with
```
sudo userdel -r YourOldUserName
```
This will delete the account as well as your old home folder.

PS: If the above mentioned folders, settings' files, etc. give you any trouble with ownership (ie. owned by YourOldUserName):
```
sudo chown -R YourNewUserName: /path/foldername
```
for folders and
```
sudo chown YourNewUserName: /path/filename
```
for files.

---

### Post by sergio91pt on 2011-10-12
My best guess is that the problem is on your compiz config, so can you try this on your old account:
```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by crozar on 2011-10-13
ive got the same issue, my unity dock is gone after making an update from the update manager , really weird , ive made a new user  it works now , _**but restarting compiz didnt help**_

 > unity-panel-service: no process found

warning: no Display variable set, setting it to 0 unity-panel-service: no process found


these are the errors i took note of what happens after trying to resset unity or restart compiz and anything else.

i even tried to run unity

---

### Post by autra on 2011-10-13
Indeed, I am always very careful while playing with compiz, because it is still quite buggy. Some options are juste incompatible with each other, and sometimes you don't know it, and some other will work on a friend's computer, and just make yours crash... (because of graphic cards drivers, of random quality on Linux)
So I also had this kind of trouble a couple of time.
My technic is to:
-Install Unity 2D, to be able to have a GUI in case of compiz crash
-Or keep gnome 2 _without compiz_ (then you can choose which GUI to use at login, be careful Gnome 3 and unity are NOT compatible)
-Do one change at a time, and write in my mind all that I did (and all the conflicts it raises) to be able to roll back.
-Then if you have a problem, you log in with a non-compiz gui to start ccsm and try to solve things up. You can also edit conf files yourself in command line, but it takes much more time to figure out where things are, so you might want to avoid this (though I had to deactivate compiz by editing one file once - can't remember where - before I had a gui without compiz)

To conclude, it's normal changing of user solved the problem (you seems to have been surprised of that in your mail). This is typically a conf problem (which should not happen, I agree!)
And yes, the graphical layer is on top of pretty much everything. That's cool, because you can't rely to gui as much as command line environment, therefore you always have a way to get out of trouble.

Congrats for solving this anyway !:popcorn:

---

### Post by yzarc1 on 2011-10-18
I had this problem, and I found a solution which eliminates the need to create a new user.

My file ~/.config/compiz-1/compizconfig/config contained
```

[general_ubuntu]
profile = 

[gnome_session]
profile = 

```My solution was
```
cd ~/.config/compiz-1/compizconfig/ ; mv config config.old
``` after which I could log in.  No need to create a new user.

---

