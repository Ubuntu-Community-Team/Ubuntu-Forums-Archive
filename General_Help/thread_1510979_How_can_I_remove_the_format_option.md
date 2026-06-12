---
title: "How can I remove the format option?"
date: 2010-06-16
forum: General Help
---

### Post by giddyup306 on 2010-06-16
Hello,

I would like to disable the option to format a hard drive on the drop down menu in computer.  The reason being is that it is too close to the safely remove hardware option.  I have one drive with about 15 years of stuff on it that I just use as a backup, and I don't want to accidentally hit the wrong button.  What I was thinking of doing is going to that section of code and commenting that line out (that way I can just uncomment it if I want to format with the GUI tool).  So my question is where can I find the code for that module?

Thanks in advance.

---

### Post by warfacegod on 2010-06-16
Could you post a screenshot? I looked in "Computer" and I'm not seeing what your talking about.

---

### Post by elliotn on 2010-06-16
Ubuntu have no format option? Screenshot please

---

### Post by giddyup306 on 2010-06-16
> **warfacegod said:**
> Could you post a screenshot? I looked in "Computer" and I'm not seeing what your talking about.

Sorry about the quality, I had to take the pic with my phone. This is for a thumb drive (an external HD has the format and safely remove feature next to each other). 

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/format.jpg[/IMG]

---

### Post by philinux on 2010-06-16
> **elliotn said:**
> Ubuntu have no format option? Screenshot please

Just happened to have this on screen.

---

### Post by john newbuntu on 2010-06-16
When you hit that option, it asks you for a reconfirmation.  Does that make you feel better or would you still opt for a removal?

---

### Post by giddyup306 on 2010-06-16
> **john newbuntu said:**
> When you hit that option, it asks you for a reconfirmation.  Does that make you feel better or would you still opt for a removal?

I just formatted a drive the other day, and it didn't ask me for a confirmation.  I still get nervous with it being there. ):P

EDIT:  I just formatted a flash drive for the heck of it...  it did ask me for a confirm, but in the past it has not. *shrugs*

---

### Post by nothingspecial on 2010-06-16
You might be able to do it with nautilus-actions. It is a tool for adding things to tour right click menu. I don`t know if it can remove existing options though.

---

### Post by giddyup306 on 2010-06-18
ttt

---

### Post by dcstar on 2010-06-18
IMHO the format option should only be available to admin rights users.

I have just created a couple of bug reports for Nautilus and gnome-disk-utility as these packages allow users without System Administration privileges the ability to format and I consider that a major security hole:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/595825](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/595825)
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/595823](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/595823)

Feel free to add to the "This affects me" list.

---

### Post by giddyup306 on 2010-06-20
> **dcstar said:**
> IMHO the format option should only be available to admin rights users.

I have just created a couple of bug reports for Nautilus and gnome-disk-utility as these packages allow users without System Administration privileges the ability to format and I consider that a major security hole:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/595825](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/595825)
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/595823](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/595823)

Feel free to add to the "This affects me" list.

Thanks for the reply David.  I think this is a great idea!  Do you mind if I put those links in my sig? I went ahead and added myself to the "This affects me" list.

Thanks,

Mike

---

### Post by dcstar on 2010-06-20
> **giddyup306 said:**
> Thanks for the reply David.  I think this is a great idea!  Do you mind if I put those links in my sig? I went ahead and added myself to the "This affects me" list.

Thanks,

Mike

I have basically been shot down for reporting this behaviour as a security bug, apparently it is ok to allow non-admin users the full capability to format a storage device just because it is plugged into the outside of a computer rather than being on the inside.

IMHO there should be a mechanism for disallowing this format capability, but it does not exist at the moment because it is not perceived as a problem.

---

### Post by giddyup306 on 2010-06-20
> **dcstar said:**
> I have basically been shot down for reporting this behaviour as a security bug, apparently it is ok to allow non-admin users the full capability to format a storage device just because it is plugged into the outside of a computer rather than being on the inside.

IMHO there should be a mechanism for disallowing this format capability, but it does not exist at the moment because it is not perceived as a problem.


That's funny.  I mentioned this to one person who I know runs Lucid, and he agrees that there should be some sort of limit on it.

His exact words: "this feature has always seemed a little odd to me, its something they  certainly need to fix in *nautilus".

Also since Ubuntu is an Open Source program, I think I should be able to manually disable the option myself. *shrugs*

---

### Post by giddyup306 on 2010-06-24
ttt

No ideas?

---

