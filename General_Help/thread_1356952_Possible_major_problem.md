---
title: "Possible major problem"
date: 2009-12-16
forum: General Help
---

### Post by Danwhelan on 2009-12-16
Hi there - I hope some one can help...  ubuntu Karmic 9.10 from USB. 

This started with my desktop icons disappearing...  no major problems otherwise... just went away. 

I thought it was a problem with Nautilus.. so I ran it from the ternimal (don't ask why) I noticed that parts of it failed to load, copied the problem into a google search and the general consensus was to reinstall Nautilus.

Then I noticed that Sudo wasn't either loaded or installed. 

I rebooted.. 

Sudo worked fine... I reinstalled Nautilus.

Rebooted as nothing seemed to change. 

Now I get to the login screen... login.. then go back to the login screen... 

It's like watching the sound of music again and again.. only more depressing. 

I can boot into Ubuntu using the USB stick that I made to install it in the first place and to be honest it's fine - I just miss my mail... aside from that all is fine... no hardware problems. 

I think that I may have to reinstall the whole thing.. however I don't want to... that's a windows fix!!! 

Can any one help... my old drive is there under places... listed as 77gb filesystem. 

Also I'm trying to copy my mail folder accross to my expansion drive - just in case. 

However there is an x ont he folder and the user is listed as 1000 - user #1000

Help please all you experts you. 

Thanks 

Dan

---

### Post by Danwhelan on 2009-12-16
Here I think is the other problem 

In the terminal... I go to my old main drive where my files were stored..  a DIR produces

ubuntu@ubuntu:/media/989f8d7c-d337-4a4e-b3aa-3cac62b32ff0/home/danny$ dir

Desktop    Downloads         hosting  Mail   Pictures  Templates    Videos    You\ add\ the\ 
colour Documents  examples.desktop  Junk     Music  Public    Ubuntu\ One  winetricks


I then try and access the Mail folder. 

ubuntu@ubuntu:/media/989f8d7c-d337-4a4e-b3aa-3cac62b32ff0/home/danny$ cd mail

I get 

bash: cd: mail: No such file or directory

This folder has the owner "1000 - user #1000" in the permissions.... and a cross over it.

Please if anyone knows what this is or how to get in to the folder I'd appreciate... 

I've tried every version of chown and chmod I can think of... put it this way... if any of you have folders that have odd file permissions... that was probably me - sorry!

Many thanks 

Dan

---

### Post by Ahadiel on 2009-12-16
> **Danwhelan said:**
> Here I think is the other problem 

In the terminal... I go to my old main drive where my files were stored..  a DIR produces

ubuntu@ubuntu:/media/989f8d7c-d337-4a4e-b3aa-3cac62b32ff0/home/danny$ dir

Desktop    Downloads         hosting  Mail   Pictures  Templates    Videos    You\ add\ the\ 
colour Documents  examples.desktop  Junk     Music  Public    Ubuntu\ One  winetricks


I then try and access the Mail folder. 

ubuntu@ubuntu:/media/989f8d7c-d337-4a4e-b3aa-3cac62b32ff0/home/danny$ cd mail

I get 

bash: cd: mail: No such file or directory

This folder has the owner "1000 - user #1000" in the permissions.... and a cross over it.

Please if anyone knows what this is or how to get in to the folder I'd appreciate... 

I've tried every version of chown and chmod I can think of... put it this way... if any of you have folders that have odd file permissions... that was probably me - sorry!

Many thanks 

Dan

File and folder names are cAsE-sEnSiTiVe.

Mail != mail

---

