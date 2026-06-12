---
title: "I think I've lost permissions in ~/"
date: 2011-10-27
forum: General Help
---

### Post by kenrmcl on 2011-10-27
I'm currently running Xubuntu 11.04. It worked fine right from the initial installation (upgrade from 10.10). It's installed on my old Dell desktop, which I use as a server & occasional quick email checks; Google searches; etc.

I usually leave it running and just come back from to it from time to time, or access it remotely via RDP.

Over the last couple of weeks I've installed a few things mostly trying to get Samba working (without success). I didn't log out for about a week and all was working well.

Since I didn't need the machine I turned it off again and rebooted each morning for awhile and just checked a few blogs on Firefox. Still no problems noted.

A couple of days ago I flashed up a terminal from the menu (Terminal 0.4.8) and found I had no Bash prompt. Claws-Mail runs puts the CPU at 100%, but downloads nothing. Thunar opens a window from the Home desk icon (and any other folder) but shows nothing inside it.

Reinstalling packages (CLaws-Mail, Thunar, Terminal) didn't work, copying files from /etc/skel made no difference. Google gave a few leads for individual issues but not all symptoms together, and none of the suggestions worked. I've obviously hosed something but I don't know what. My computer may even have been this way for a week or more but I didn't find out since I only used FireFox which is working OK.

I don't really know where to look although, as the subject line says, I think I may have upset the permissions or perhaps some authority mechanism. Any ideas on where to look or what to look for will be gratefully accepted. 

BTW, Alt+F2 allows me to run xterm without any problems. Bash shows up & I can see all of my files; move from directory to directory; edit what I need to; etc.

Thankyou,
Ken

---

### Post by decoherence on 2011-10-27
You say you can edit what you need to. If you can edit files, then you have write permission on them. In any case, it's easy enough to see whether your permissions are messed up. Hit Alt F2 to bring up xterm and type 'ls -l'

You should see your username beside the various files and directories it lists. I don't know for certain what Ubuntu's umask is, but on my system files in my home directory have the following permissions

-rw-r--r--

and directories have 

drwxr-xr-x

---

### Post by kenrmcl on 2011-10-27
> **decoherence said:**
> You say you can edit what you need to. If you can edit files, then you have write permission on them. 

Of course. It's obvious isn't it. I should have thought that one through a bit more. 

My files/directories all appear to have permissions as you describe except .Xauthority which has -rw-------. Google tells me is correct.

I've created a new user account as a test, and it works fine. I can't replicate the symptoms on it. This leads me to think I've corrupted a configuration file somewhere, but have no idea what it might be nor where to start looking.

I've noted that one of the things that doesn't work is the command 
"exo-open --launch TerminalEmulator", whereas a direct "xterm" is fine.

Also, if I open a USB ram stick, Thunar shows a blank window. If I then go back up the tree to the folder above, and then down again, I get a normal listing. However it still won't work with my home folder. It's got me confused, that's for sure.

Thanks for your assistance decoherence. It's much appreciated.
If you can think of anything else, then please let me know.

---

### Post by decoherence on 2011-10-27
Sorry, I can't think of anything off the top of my head.

I don't know why Thunar is not showing a directory listing, or why it does on your USB key when you go up a level and back down. Frankly, if I saw that kind of behavior, I probably wouldn't even bother troubleshooting it -- I'd just chuck Thunar and XFCE out the window (I already have, in fact, because it was doing other silly things.)

That said, you can try renaming some config files and see if that fixes things. I don't recall what they're called or where they are -- my lone Ubuntu (with Xubuntu) computer is on the site I'm working at. I'll be there in an hour or so, so if you haven't found anything by then I'll post back.

ADD:

ok i'm on site now. In the .config folder I renamed the xfce4 and Thunar directories and it gave me a 'clean' xfce session. So you might give that a try and see if it fixes anything. Good luck!

Now I think I'll give xfce another chance. I really like it except for when it does random stupid things.

---

