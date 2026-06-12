---
title: "ATI drivers not working (blocked by Nvidia drivers)"
date: 2006-05-14
forum: General Help
---

### Post by Dr_Deadmeat on 2006-05-14
I have some issues with my ATI drivers... I had a Nvidia GeForce 4 440mx installed on my computer, but I have now switched to a ATI Radeon 9200, but when I tries to install the fgrlx drivers I can't install them, and I cannot uninstall the nvidia-glx package... Is it a way to do this? (Like shutting down gnome, and using the terminal to uninstall and install the drivers). I only have issues with open gl. Everything else works fine...

I have no idea about what to do, and it is really frustrating not to be able to play 3d games sometimes...

---

### Post by tseliot on 2006-05-14
sudo dpkg-reconfigure xserver-xorg

and when it asks you which videocard you want to use select the Ati and the "ati" driver.

After it finishes you have to log out and press CTRL+ALT+Backspace.

Log in and install the Ati proprietary driver. This time it should work.

---

### Post by Dr_Deadmeat on 2006-05-14
[QUOTE=tseliot]sudo dpkg-reconfigure xserver-xorg

and when it asks you which videocard you want to use select the Ati and the "ati" driver.

After it finishes you have to log out and press CTRL+ALT+Backspace.

Log in and install the Ati proprietary driver. This time it should work.[/QUOTE]

It didn't worked, and i got a error message wich says that tha pre-installation script returned error status 2 (or something like that, translated from Norwegian)...

The conclusion is that it didnt worked, and I still need help... Please ](*,)

---

### Post by tseliot on 2006-05-14
1) post the content of your /etc/X11/xorg.conf
2) post the output of this command:
```
lspci
```

---

### Post by Dr_Deadmeat on 2006-05-14
[QUOTE=tseliot]1) post the content of your /etc/X11/xorg.conf
2) post the output of this command:
```
lspci
```[/QUOTE]

Here is the output for lspci

```

andreas@andreas:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
0000:00:0d.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
andreas@andreas:~$

```

I hope this help (I attached my "xorg.conf" file)

I managed to choose fglrx drivers in xorg.conf reconfigure, but it still did not fix my problem

---

### Post by tseliot on 2006-05-14
set the driver to "ati" so as to reproduce the error.
then type:
```
sudo /etc/init.d/gdm restart
```

answer "No" if it asks you to see the output to debug it.

then type:
```
sudo /etc/init.d/gdm stop
```

```
sudo cp /var/log/Xorg.0.log /home/your_username/
```

(make sure the "X" is a capital letter)
(replace "your_username" with your "your username")

then type:
```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "vesa" in the Section Device of your xorg.conf

Press CTRL+X to exit (save it when it asks you)

then:
```
sudo /etc/init.d/gdm restart
```

Now you should  have a graphical environment up and running.
And you can post your /home/your_username/Xorg.0.log

---

### Post by Dr_Deadmeat on 2006-05-14
I have now done what you have asked for and I wil uppload the file as an attachement. Im sorry that I replied late, but I had some crucial work to do first... Anyway, is it a way to fix this? (BTW: I use something called mesa to 3d acceleration or something like that)

---

### Post by Dr_Deadmeat on 2006-05-14
I've forgot to upload file ](*,)

---

### Post by tseliot on 2006-05-14
Your log says that you have 2 devices:
```
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon RV280 [Radeon 9200] rev 1, Mem @ 0xe0000000/27, 0xf9000000/16, I/O @ 0xe000/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x5941) rev 1, Mem @ 0xe8000000/27, 0xf9010000/16
```
sudo nano -w /etc/X11/xorg.conf

set the driver to "ati"

and set the BUSID to 1:0:1 (if your current BUSID is 1:0:0)

Then save the file and exit.

Type:
```
sudo /etc/init.d/gdm restart
```

and see if anything changes

---

### Post by Dr_Deadmeat on 2006-05-14
I&#836;'ve done that and I've just ruined my Xserver so now I am on my working laptop writing this... I forgot to take backup, but is it enough to take a:

```

sudo dpkg-reconfigure xserver-xorg

```

Or have I ruined my whole computer now?

---

### Post by Dr_Deadmeat on 2006-05-14
It worked with the reconfigure command, but I still don't have 3d acceleration... Please help me :cry:
I am desperate.

---

### Post by Dr_Deadmeat on 2006-05-15
C'mon... Is it no one who can help me?

---

### Post by tseliot on 2006-05-15
Try setting the driver to "radeon" (instead of "atii", vesa, etc.) in your xorg.conf

But I'm not an expert in this field (I deal with Nvidia cards)

---

### Post by Dr_Deadmeat on 2006-05-15
[QUOTE=tseliot]Try setting the driver to "radeon" (instead of "atii", vesa, etc.) in your xorg.conf

But I'm not an expert in this field (I deal with Nvidia cards)[/QUOTE]

When I did this my screen became just screwed... (It happened when changing to ati driver too, but not on the fglrx driver) I will uppload a screenshot to show my desktop when I ran the radeon driver (the same happened with the ati driver)

---

### Post by Dr_Deadmeat on 2006-05-15
Ok, now I've got the screenshot sorry for the delay...

---

### Post by tseliot on 2006-05-16
That goes beyond my knowledge, try this guide and see if it gives you 3d acceleration:
[http://ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver]("http://ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver")

and this one:
[http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+mesa]("http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+mesa")

---

### Post by Dr_Deadmeat on 2006-05-16
It worked at last... I'd just had to reinstall the ATI drivers from "apt-get" and then things worked out... Thanks for the help =) I really appreciate it (but expect me to post some question about the nVidia card on my laptop too... I can't get that to work either ](*,) ) Anyway... Thanks for all help I really appreciated it :)

---

