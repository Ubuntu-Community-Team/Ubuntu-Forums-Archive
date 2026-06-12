---
title: "Problems scannig with dx9400F(+server doesn't appear in network)"
date: 2010-05-26
forum: General Help
---

### Post by lyssion on 2010-05-26
Hello everyone, I have installed 10.04 server, and I have 1 printer(hp) and 1 all-in-one epson, both print fine. The problem is as always scanning with my epson. At first I couldn't even get it to find the scanner, i fixed it, then i managed to make it work without using sudo too.
But now i am facing a problem that i spent more than 6hours looking for a solution, reading other posts and i think i need your help (i am fairly new to linux). (keep in mind in case i messed up, but i have added udev rules to let me scan without root)

When i do scanimage > test.jpeg, and I go over to my windows pc, opening that folder (have it shared via samba), there is no program that can open the image. I also tried to scan with phpsane, see if i could get something different and the result is always a small black square. I don't know if its drivers conflicting or permission problems, but I can't figure it out alone:S

I have also installed iscan, but when i type iscan in the console i get" (iscan:1470): Gtk-WARNING **: cannot open display:
". I guess that's cause I don't have a desktop edition of ubuntu installed? I did also (in the last few minutes) comment out epson and epson2 in /etc/sane.d/dll.conf and epkowa is added.

Scanimage -L gives:
```
device `epkowa:usb:001:002' is a Epson Stylus CX9300F/CX9400Fax/DX9400F flatbed scanner
```
So i don't know what to do anymore, any idea?thanks :)



and 1 side issue, I am not sure if this is caused by whatever I did to fix the scanner, but when I look from the network for my ubuntu server, I cannot find it. I can see all the windows computers but not that. However just typing \\homeserver in the address opens up all the samba folders and i have normal access. Any idea what might have caused this?

Thanks in advance and sorry for the long post.

---

### Post by lyssion on 2010-05-26
I dont know how, but server now appears over network... i tried twice (after reboot) and worked both times. so i guess that's not an issue anymore.

But as for the scanner i still have no idea. If it can help anyone give my some tips. Everytime i scan, the image that results (that i can't open) is always 25,5MB. Despite being a jpeg. I don't know, seems like too much.

When i only run " scanimage " instead of "scanimage > test.jpeg"
I see a lot of text in my console window. It's like its the picture,but in data. But then why doesn't the picture appear normally when i used the > test.jpeg ?:S

---

### Post by lyssion on 2010-06-01
Bump!

Also, after some more reboots the server appears on network tab almost half of the times its rebooted.

---

