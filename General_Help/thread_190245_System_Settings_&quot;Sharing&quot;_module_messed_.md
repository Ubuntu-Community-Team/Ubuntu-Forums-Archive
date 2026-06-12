---
title: "System Settings &quot;Sharing&quot; module messed up?"
date: 2006-06-06
forum: General Help
---

### Post by msak007 on 2006-06-06
I just resolved an issue I was having with the "Display" System Settings module, but I'm now having a problem with the "Sharing" module. When I click on "Sharing", I get 3 options: "Desktop Sharing", "File Sharing" and, "Local Network Browsing". When I click on "File Sharing", the output is what's in the screenshot. Even with Administrator access, I can't make any changes because everything is grayed out (and looks as if part of it is cut off at the top). Anybody experience the same issue or have any suggestions?

---

### Post by givré on 2006-06-06
did you try running it with sudo in a terminal.
You will also be able to see the output

---

### Post by msak007 on 2006-06-06
I'll try that when I get home, as I'm at work now. What's the command for System Settings? Alternatively I could run kdesu kcontrol, as that would have all the same modules right? I notice that you're using Ubuntu, I'm kinda interested to see if any other Kubuntu users are experiencing the same issue. I know kcontrol has a separate entry for Samba, but I'd like to get this module to work.

---

### Post by givré on 2006-06-06
I think it's systemsettings (i'm at work to :wink: ) but autocompletation is your friend.

EDIT:autocompletation will not work if you put sudo before, try without first

---

### Post by msak007 on 2006-06-06
Ok so I tried using "systemsettings", and here's the output that I got when it opened up and as I subsequently clicked on "Sharing":

[1] 6336
motasim@Xaser:/$ X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
adding Desktop Sharing /usr/share/applications/kde/kcmkrfb.desktop
ScimInputContextPlugin()
adding File Sharing /usr/share/applications/kde/fileshare.desktop
adding Local Network Browsing /usr/share/applications/kde/lanbrowser.desktop

Clicking on the individual options within "Sharing" doesn't change any of the output in the terminal, and neither does clicking on the button to get Administrator access. I see that it's the file "fileshare.desktop" that is supposed to load. If someone isn't having a problem with this module, would I be able to replace mine with a working one?

---

### Post by sushi on a grill on 2006-06-06
i have the same problem up til now...


i just found this from another thread and its working for me right now


```
sudo apt-get install nfs-kernel-server samba
```

---

### Post by msak007 on 2006-06-06
Thank you so much! That worked like a charm. I searched and couldn't find anything, so thank you for that. Is this a bug in Kubuntu?

---

### Post by mnphenow on 2006-06-10
Indeed I was seeing the same behavior.  The suggested fix also worked for me.  This does not seem like appropriate default behavior.

In general, the UIs of the various control center tools are not well laid out.  I often have to maximize them to get things (particularly the "Administrator Mode," "OK," "Apply," and "Cancel" buttons) in view.  I haven't made any out-of-the-ordinary configurations.  I think this is something that really needs to be addressed.  I can handle it, but I want to see *buntu widely adopted and behavior like that would turn most people away.

---

### Post by kag on 2007-02-20
I'm pretty much on a default Kubuntu 6.10 install. I only installed the nvidia drivers and changed my resolution. I'm having the same problem.

---

