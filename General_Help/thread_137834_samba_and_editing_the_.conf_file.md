---
title: "samba and editing the .conf file"
date: 2006-02-28
forum: General Help
---

### Post by lordjeff on 2006-02-28
Hola gang, I'll start by admitting my noob'ness. :) 
Once I was mildly comfortable with Xandros, I decided to give a different distro a try.  I originally went to Debian itself and then found uBuntu.  Very much prefer the ubuntu distro \\:D/ over the deb one so far (figured I'd give background so u'd know where i'm coming from).

However, I'm a total greener when it comes to finding things in gnome.  I was looking to configure Samba for filesharing with my windows network.  I went into /etc/samba/smb.conf with the file browser.  However, it's listed as read-only, so I don't seem to be able to edit it?  

I tried logging in as "root" at the main login, however, it says I can't login as root from that screen.  So how do I edit samba settings?  If there's a gui/gnome type app i can install to allow this; I'm fine with that too hehe.  I need to do more then setup shared drives I want to edit some of the settings. ;) 

Thanks guys for any help you can offer...

---

### Post by soulestream on 2006-02-28
ubuntu uses sudo. 

so if you use vi to edit smb.conf then

sudo vi /etc/samba/smb.conf

for gedit

sudo gedit /etc/samba/smb.conf

then enter your user password

soule

---

### Post by lordjeff on 2006-03-01
thanks, that was what I didn't know.  Never encountered sudo up t'ill now. :-D

---

### Post by lordjeff on 2006-03-01
So question #2.  I am running a little workgroup.  When I try and browser the shares on the ubuntu machine from a windows machine within the same workgroup; I can't get up a list of drives.  The drives themselves are set to be "public".  However, past that I'm not sure where to go next.:cry:

---

