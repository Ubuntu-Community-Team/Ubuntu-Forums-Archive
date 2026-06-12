---
title: "Download issue"
date: 2012-04-17
forum: General Help
---

### Post by TominMO on 2012-04-17
Hi all,
New user here, first post. I have 11.10 loaded by itself on a 2004 Dell Inspiron 8600 laptop. Battery had died awhile ago, wasn't using it, so decided to make it my Ubuntu rig to check this whole world out. Using XP on my desktop.
 
So anyway I downloaded a game called glchess from the Ubuntu Software Center. I believe it installed automatically--but there is no icon anywhere to play it. I can find the files under file system/usr/share, but haven't figured out how to play the game, or if I actually need to do an install (i.e. maybe the files were just downloaded, not installed after all).
 
Any thoughts? Much appreciated. This aside, I am enjoying fooling around w/Ubuntu as my coffeeshop computer.

---

### Post by MG&amp;TL on 2012-04-17
No, normally the Ubuntu Software Centre downloads and installs the package for you. I imagine it's a bug in the software. :(

To help us debug the problem, could you open a terminal (in the dash, purple box thing with a prompt), and enter:

```
glchess
``` 

Thanks!

---

### Post by gandalf3 on 2012-04-17
did you look in the dash? (the Ubuntu icon at the top of the screen)
open the dash and type "glchess" in the search bar, and see if anything comes up.
hope this helps.

---

### Post by TominMO on 2012-04-17
> **MG&TL said:**
> No, normally the Ubuntu Software Centre downloads and installs the package for you. I imagine it's a bug in the software. :(
 
To help us debug the problem, could you open a terminal (in the dash, purple box thing with a prompt), and enter:
 
```
glchess
``` 
 
Thanks!Thanks, did that. That's how new I am, didn't know it might be necessary! The terminal gave me the instructions to type in "sudo apt-get install glchess". Did so, and it performed some installs. Still needs 4,691 kb of archives, so I guess this stuff would be online. But I can't go online on my laptop right now--I'm doing everything simultaneously on my desktop (online) and the laptop (offline). But this is looking promising, so the next time I can get to the coffeeshop or somewhere else that has wifi, I will pursue this. Thanks!!! :)

---

### Post by MG&amp;TL on 2012-04-17
Odd. It seems that Ubuntu Software Centre didn't install glchess properly for some reason.

Sorry for the inconvenience. Did USC give any error messages, or just complete successfully?

---

### Post by TominMO on 2012-04-17
> **MG&TL said:**
> Odd. It seems that Ubuntu Software Centre didn't install glchess properly for some reason.
 
Sorry for the inconvenience. Did USC give any error messages, or just complete successfully?When I read the reviews for this program, one person mentioned that he did not get an icon either. Apparently he had the same issue, and may have been a noob like me as well.
 
No error msgs, just apparently could not complete the task due to not being online at the moment.
 
BTW, how can you get the Terminal to be an icon on the desktop?

---

### Post by MG&amp;TL on 2012-04-17
If you're using Unity, it might be wiser to put it on the Launcher. Just drag and drop it from the dash to the launcher. To remove things from the launcher, right click, Unlock from Launcher.

---

### Post by TominMO on 2012-04-17
> **MG&TL said:**
> If you're using Unity, it might be wiser to put it on the Launcher. Just drag and drop it from the dash to the launcher. To remove things from the launcher, right click, Unlock from Launcher.:) Dragged it into the Launcher, but no icon! Just a blank space. But it works! Then dragged it from the dash to the desktop, so I at least have an icon. Then right-clicked the "invisible icon" on the launcher, and de-selected "keep on launcher". So now it's on my desktop. Shoulda bin able to figure this out myself. :confused:
 
Thanks for the help all, I'll re-try the install when I can get to a wifi site.
 
EDIT: I should mention that I don't want to use my cable internet connector to switch back and forth between the desktop and laptop, as it seems to have trouble with the switches, and it takes me some stumbling around to get it working again on whatever computer I have just plugged it into.

---

### Post by MG&amp;TL on 2012-04-17
It's a bug, some apps don't show up-the Unity devs are on it, I believe. 

Oh well, whatever works fr you. :)

---

### Post by gandalf3 on 2012-04-17
> Dragged it into the Launcher, but no icon! Just a blank space. But it works!that happened to me a few times.. it fixed itself when i rebooted though..
if it doesn't, and you want something besides a blank space, you can try downloading main menu from the repositories

sudo apt-get install main menu

i think that's the right command anyway..
if it's not you can just do it graphically from the software center.
then in the main menu, navigate to your application, (probably under games)
double click, and click on the little icon in the dialog box.
browse to a image you want to use as your icon, and click "open"
then reboot.
if that doesn't work, i don't know of anything else you might try..
hope this helps!

---

### Post by TominMO on 2012-04-17
> **gandalf3 said:**
> that happened to me a few times.. it fixed itself when i rebooted though..Interesting...and wacky. I also had the issue of my pad not working, as I have seen others write about elsewhere, but it has been working lately.

---

