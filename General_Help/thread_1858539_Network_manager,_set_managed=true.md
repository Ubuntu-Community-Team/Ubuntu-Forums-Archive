---
title: "Network manager, set managed=true"
date: 2011-10-12
forum: General Help
---

### Post by 1keith1 on 2011-10-12
My current situation:
I am using a Thinkpad T420  and My wifi works fine but Ethernet does not, it spends minutes trying to connect and then gives up. 

Well when I look at my nm-system-settings.conf file I see that managed=false, and it should be true, as is stated[ here]("http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html").

Heres what terminal gives when I try to gedit:

```
 sudo gedit /etc/NetworkManager/NetworkManager.conf

(gedit:2264): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.A5M22V': No such file or directory

(gedit:2264): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

It then opens the file and I see that managed=true, and I can't gedit nm-system-settings.conf either so when I go to that file managed=false still.

---

### Post by dino99 on 2011-10-12
take time to watch and understand what that link says:

sudo gedit /etc/NetworkManager/nm-system-settings.conf


.....

---

### Post by 1keith1 on 2011-10-12
I should have mentioned why I typed in a different command, if I try to edit nm-system-settings.conf, even though I can view the file in the folder, a blank file will come up when using sudo gedit. I looked in the comments of the link and for 11.04 the command I used is what you are supposed to use I guess. I'm confused because I try to edit a file that doesn't exist and it works, but when I try to edit nm-system-settings.conf which does exist I again get a blank file because its not found, and I am punctuating and typing file names correctly.

Edit: ```
$ sudo gedit /etc/NetworkManager/nm-system-settings.conf
[sudo] password for keith: 

(gedit:1784): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Q5WD3V': No such file or directory

(gedit:1784): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

---

### Post by cryptotheslow on 2011-10-12
Use:

```
gksudo gedit
```
or
```
gksu gedit
```


gksu / gksudo should be used for graphical applications rather than su / sudo.

Not sure that will alleviate your problem but it is best practice.

---

### Post by 1keith1 on 2011-10-12
> **cryptotheslow said:**
> Use:

```
gksudo gedit
```
or
```
gksu gedit
```


gksu / gksudo should be used for graphical applications rather than su / sudo.

Not sure that will alleviate your problem but it is best practice.
I tried that, I keep getting similar error messages in kernel after I save and close the file. (for editing both files, nm-system-settings.conf and NetworkManager.conf)

```
$ gksudo gedit /etc/NetworkManager/NetworkManager.conf

(gedit:4009): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4009): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DY462V': No such file or directory

```

---

### Post by cryptotheslow on 2011-10-12
Hmm....  but all those two errors mean is that it is failing to update root's "Recently Used" files list. That just gets used for things like the "Recent Documents" list in "Places".

As it's a Gtk error you could try editting the file in the Terminal instead.

So:
Press Ctrl+Alt+T  to bring up a Terminal window.
Then:

**[FONT=Arial][SIZE=2]```
sudo nano [B]/etc/NetworkManager/nm-system-settings.conf**
```
[/SIZE][/FONT][/B]
That just open up the file in the nano text editor. So make your changes then press Ctrl+X to exit, choosing Y (yes) to save changes.

---

### Post by 1keith1 on 2011-10-12
Odd, maybe me getting my ethernet connected wasn't related to that, nm-system-settings.conf still says managed=false but now my ethernet is working.

My only two guesses are that when I updated (through wifi) a couple of things (which I think were just office suites) fixed it or that maybe when I opened networkmanager.conf I changed true to false, then back to true, and restarted.

Problem fixed.

---

### Post by cryptotheslow on 2011-10-12
Good stuff. Please mark the the thread as SOLVED using the Thread Tools option at the top of you opening post.

---

