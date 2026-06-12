---
title: "Problem with Permission"
date: 2009-09-04
forum: General Help
---

### Post by zoejoe on 2009-09-04
Hi everyone,
I've changed mode of my home folder to 777 -R, and then, totem, and firefox does't work correctly. 
Then I go to root account and open Firfox, it worked, but totem has a problem and crashed when I open a movie file. This is the console report, please help me, I have no idea about this :((

```
[root@localhost ~]# firefox
[root@localhost ~]# totem

** (totem:4257): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 50 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[root@localhost ~]#

```

I've got this trouble just in this morning, after I used this command:
su 
*****
chmod 777 -R /home/phong

And I use Mandriva linux 2009

---

### Post by SoftwareExplorer on 2009-09-04
Does it work if you do ```
sudo chown -R phong:phong /home/phong
sudo chmod 644 /home/phong/.dmrc
sudo chmod 644 /home/phong/.ICEauthority
```?
This will protty much set your home folder to the normal permissions.

---

