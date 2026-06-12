---
title: "evolution mail import, from another evolution"
date: 2006-04-20
forum: General Help
---

### Post by jezjones on 2006-04-20
Hi everyone,

I have been using ubuntu with evolution for my mail, on my desktop for a over a year. I have lots of mail and lots of folders.
Late last year i got a new laptop and i have the same combination on there.
The email is using pop3 so what i have been doing is letting the desktop machine delete mail from the server when it gets it, but on the laptop to leave it on the server. So the result is that i get email on my laptop but my email store is my desktop, and the email on the server is kept to a minimum.

Now i have decided that since the laptop is most powerful, i have decided to get rid of my desktop.

I have copied my entire .evolution folder from the desktop to a usb key, but i am cautious of just pasting it in place on the laptop and overwriting the one that is there already.
I guess i have nothing to lose, since what emails are on the laptop should be in the stuff i am pasting.

Can anyone give me any tips of how to migrate evolution across machines.

Thanks,

Jez

---

### Post by dcstar on 2006-04-20
[QUOTE=jezjones]
......
I have copied my entire .evolution folder from the desktop to a usb key, but i am cautious of just pasting it in place on the laptop and overwriting the one that is there already.
I guess i have nothing to lose, since what emails are on the laptop should be in the stuff i am pasting.

Can anyone give me any tips of how to migrate evolution across machines.

Thanks,

Jez[/QUOTE]
Close Evolution, rename the existing .evolution folder, paste in the other one, and start up Evolution.

---

### Post by jezjones on 2006-04-20
Thanks for the speedy reply.

I have re-named the desktop .evolution folder on the usb key to "evolution_desktop" and pasted it into /home/[user]/.evolution.

The app was closed at the time, but on restarting it there doesn't appear to be any changes.

What i am trying to do is merge whats on the laptop already with all the stuff from the desktop. If this is not possible, i will overwrite with the desktop stuff, but i was hoping to find a non-destructive way. I think i am worried about system settings being different on the two machines, for instance there are files in .evolution like addressbook.db and beagle_changes.db. 
Maybe i am being too cautious, but if the laptop will be my 'production' machine i want to be careful to keep it working at its best.


Thanks again,

Jez

---

### Post by dcstar on 2006-04-20
[QUOTE=jezjones]Thanks for the speedy reply.

I have re-named the desktop .evolution folder on the usb key to "evolution_desktop" and pasted it into /home/[user]/.evolution.

The app was closed at the time, but on restarting it there doesn't appear to be any changes.

What i am trying to do is merge whats on the laptop already with all the stuff from the desktop. If this is not possible, i will overwrite with the desktop stuff, but i was hoping to find a non-destructive way. I think i am worried about system settings being different on the two machines, for instance there are files in .evolution like addressbook.db and beagle_changes.db. 
Maybe i am being too cautious, but if the laptop will be my 'production' machine i want to be careful to keep it working at its best.

Thanks again,

Jez[/QUOTE]
Merge is not replace, look at the directory structure in you Home folder and you will see a structure similar to this:
```
/home/dc/.evolution/mail/local/Inbox.sbd
```
Create a new folder in Evolution called "Import" (or whatever), and then you should see a .sbd directory of that name appear.

Copy all of your old /local files and folder in there, restart Evolution and (hopefully) you will then see them all.

Drag and drop them wherever you like after that.

---

### Post by jezjones on 2006-04-20
Yeah, sorry I guess the wording is very specific with this kind of thing.

Ok so now i have managed to do as you suggested. 
I had to create the imported.sbd folder myself. The creation of a folder from within Evolution didn't make a folder in /home/ulap/.evoltution/mail/local, i tried a couple of times, it only made .sbd files, although there were physical folders for some but not all of the folders i have in evolution... i wonder what basis it creates folders on... 

Anyway, aside from that it worked perfectly and it was the non-destructive result i was looking for, so thankyou very much. My mail is now migrated.


Thanks again,


Jez

---

