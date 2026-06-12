---
title: "enabled root, how to resverse negative effects?"
date: 2006-05-01
forum: General Help
---

### Post by Chris Tucker on 2006-05-01
Ok, so i enabled root. No one told me it kills gui administration programs. Quite frankly i dont even understand WHY it does this, but thats for after its fixed.

Ive changed /etc/shadow to be back to root:*:13265:0:99999:7:::  ... but still no luck on the gui applets.

What else do i have to revert to get my stuff working again? i liked sudo for not having to log out/in numerous times just to use a gui admin applet.

---

### Post by aysiu on 2006-05-01
Can you explain the steps you took to enable root? That would probably help people figure out how to reverse it.

---

### Post by Chris Tucker on 2006-05-01
all i did was sudo passwd root, set a password.... amazed at how badly that affected the system

---

### Post by aysiu on 2006-05-01
[QUOTE=Chris Tucker]all i did was sudo passwd root, set a password.... amazed at how badly that affected the system[/QUOTE] Maybe [this](https://wiki.ubuntu.com/RootSudo#head-b06dbcd33c40480dcfd3aada1ca67bbd77f80594) will help.

---

### Post by Al3xanR0 on 2006-05-02
[QUOTE=Chris Tucker]all i did was sudo passwd root, set a password.... amazed at how badly that affected the system[/QUOTE]

I have done this before, and the only issue that I had to deal with was having to add my user id to the /etc/sudoers file in order to be able to use Synaptic or Adept as root via "su" otherwise kdesu complains. Why you ask? I hate using "sudo".

---

### Post by Chris Tucker on 2006-05-02
ive tried everything that rootsudo under the wiki describes for disabling root, ive tried adding my uid with ALL in the sudoers file, no luck either way, ive even tried enabling rootpw in the sudoers file (having set a password for root again of course) but nothing works. i can still sudo, but i cant use the gui admin apps... very unnerving just having switched to kubuntu completely (fresh install!) i dont want to reinstall, theres something that enabling root does that breaks it, and if it can be broken it can be fixed! thats my motto

---

### Post by aysiu on 2006-05-02
You can *sudo*, but you can't use GUI admin apps?

In a terminal, type ```
gksudo synaptic
``` and post back any errors you get.

---

### Post by Chris Tucker on 2006-05-03
gksudo: command not found.
KDE remember? :P
kdesu kcmshell kdm
kbuildsycoca running...
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

That works just fine. I can do what i need to that way. 
kcontrol if i click on login manager, administrator mode, it will bounce back to the group page for that group of utils.
system->settings->system administration->login manager
will bring up kdesu, for the same command i typed in terminal.
when i press enter i get a dcopserver error, it says to make sure dcopserver is running, and ps aux | grep dcop  shows that it is indeed running.

---

### Post by Chris Tucker on 2006-05-07
any more ideas? :(
I *can* reinstall, its just very undesired... Any information on what files get modified when you sudo passwd root would be appreciated! from there i could work my way through to getting it working

---

### Post by Blutack on 2006-05-07
I read somewhere that you can simply go sudo passwd root and then not enter a password.  Try it and see if it locks the account.  I have to say though that I enabled root donkeys ago and have had no problems. The default system settings thing is a bit dodgy though so I use kcontrol instead (just change the command in the K menu. Hope this works!

---

### Post by Chris Tucker on 2006-05-07
kcontrol IS where the problem resides, other ways of accessing the applets kcontrol runs produce a dcopserver error message with an OK button, you click OK and the applet works reasonably, unless it has an administrator mode button, but for ones without that button, you MUST click ok before the selected app will load...
kcontrol seems to supress the message, but after a few seconds of "loading" the administrator mode for that applet, it reverts back to the intro page for that section of applets

---

### Post by Chris Tucker on 2006-05-15
Well in the spirit of not giving up, i tried what seemed to be too simple of a solution, sudo apt-get install --reinstall kcontrol. At first try it broke kcontrol worse. but after rebooting a few times i went to double check, it all works perfectly again. I have root re-disabled, but i'm going to try enabling it again later and seeing if anything changes. Reinstalling kcontrol seems to drag along some packages that fix the activation of root's harsh affects.

---

### Post by vh1 on 2006-05-16
just wondering, why do you dislike sudo?

edit: also, hello from a fellow newfoundlander!

---

### Post by Chris Tucker on 2006-05-16
i dont dislike sudo, i just use root for scp and rysnyc when needing to put files in a folder other than my /home/, and doing it from the remote end. I have no idea why people dislike sudo, when you can do sudo -i   !!

---

