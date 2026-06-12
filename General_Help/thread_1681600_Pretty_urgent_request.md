---
title: "Pretty urgent request"
date: 2011-02-04
forum: General Help
---

### Post by Kocrachon on 2011-02-04
So right now I am at work, and I need access to the windows installation on my computer at home. However, I left Ubuntu running because I didn't expect to need to do any work from it today.

Anyways, I need to access some files for work, edit them, and mail them to myself and I can't do it from Ubuntu.

Normally its not an issue, I would just restart my computer and it would boot up into windows, but the issue with that, is I need to edit grub, and to edit grub, I need to become the root, and to become the root, I need to place a terminal command.

All seems easy right? wrong, for some reason I cant send Enter through teamviewer on my Ubuntu installation right now. I can do ANYTHING except hit enter, which means I cant send terminal commands to set my grub to default launch to windows and manually restart

So I was wondering if there are any tips? I cant access Orca (for a virtual keyboard), it wants me to finish setting it up in the terminal (cant do). 

Is there a way from windows I can send a command to Ubuntu?

---

### Post by Habitual on 2011-02-04
Well, I don't know TeamViewer, so does your home computer have ssh-server installed by any chance?

---

### Post by CharlesA on 2011-02-04
If team viewer isn't working, and you don't have SSH access, you are pretty much stuck.

I know you can mount the Windows partition inside Ubuntu to access files on it, but if you can't do anything except hit "enter" then there is not much you can do.

---

### Post by Kocrachon on 2011-02-04
> **CharlesA said:**
> If team viewer isn't working, and you don't have SSH access, you are pretty much stuck.

I know you can mount the Windows partition inside Ubuntu to access files on it, but if you can't do anything except hit "enter" then there is not much you can do.

its the other way around, I cant do anything EXCEPT hit enter...

And no, i dont have SSH-server installed...If I can install it with out hte use of enter I could install it right now.

---

### Post by NFblaze on 2011-02-04
You are viewing the Ubuntu Desktop right now? Can you just mount the windows partition drives, select the files, and email them to yourself at work. Then edit them there?


Second option. Although, I dont use TeamViewer. I'm assuming that is some sort of Remote Desktop Viewer. If so, see if you can install openSSH on the Ubuntu install using Synaptic (which should require any enters if you are using the mouse).

Then download [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/"). Then SSH to your current IP address of your home computer. (Hopefully your router is configured to allow this). Then you would login to ubuntu via terminal shell. Then you could do all the regular commands such as: sudo nano /boot/grub/grub.cfg or whatever you needed.

---

### Post by Kocrachon on 2011-02-04
Ok, so teamviwer on my phone allows me to hit enter... crisis adverted!

---

### Post by The Cog on 2011-02-04
You might be able to do an Enter with this 3-key sequence:

Ctrl-Shift-U
A
Space

---

### Post by NFblaze on 2011-02-04
Seriously, save yourself some trouble install SSH. In case this happens again in the future.

---

### Post by Kocrachon on 2011-02-04
I plan to, I just reinstalled Ubuntu yesterday after I did a clean format. The reason I left it running in the first place was to download updates. Installed Teamviewer before I went to work.

It will be installed today.

---

### Post by CharlesA on 2011-02-04
Ah, glad you got it working. Don't forget to mark the thread as solved. :)

---

