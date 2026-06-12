---
title: "The Firefox browser never opens again"
date: 2011-07-31
forum: General Help
---

### Post by BSG Fan on 2011-07-31
I do not have the Firefox browser now because I had to unsintall it because was unstable, or didn't open, 
or I was clicking to open a new window, 
and the Firefox got semi-frozen, 
I closed it, and one small window opened in the top-left side all those times.

I tried to uninstall several times the Firefox but the problem continued. 

Now I supposed installed it again but now it NEVER opens.

Help
What happens?
That is the first ever time happens!

Solution?:(

---

### Post by yetiman64 on 2011-07-31
Have you tried deleting the hidden folder .mozilla (in your home folder) before doing the reinstall? 

Reinstalling does not remove this folder which contains the firefox profiles and extensions and such. If there is a corrupted profile a problem can still exist even after a reinstall of the main program itself.

---

### Post by BSG Fan on 2011-07-31
> **yetiman64 said:**
> Have you tried deleting the hidden folder .mozilla (in your home folder) before doing the reinstall? 

Reinstalling does not remove this folder which contains the firefox profiles and extensions and such. If there is a corrupted profile a problem can still exist even after a reinstall of the main program itself.
Hi, thanks for the reply.
I am searching that specific hidden file but I can not find it
As I know "my home folder" is the "File System", right?
but when I find by .mozilla I just find the "application/vnd**.mozilla**.xul+xml"  
It is?

Hey, if by error delete other Mozilla folders would the pc stop to work normal or re-start again? I remember my old times in Windows....

---

### Post by CatKiller on 2011-07-31
> **BSG Fan said:**
> 
As I know "my home folder" is the "File System", right?


No, it's /home/username

---

### Post by yetiman64 on 2011-07-31
If you are on Lucid as your profile suggests, on your panel go to Places > Home Folder, and use the key combination CTRL + H to show hidden files and folders. Look for a folder named .mozilla and delete it. It will be regenerated with new profiles etc when you reinstall and first use firefox after the reinstallation.

If you aren't using Lucid note that your home folder is at the location /home/<your-username> in the filesystem, where <your-username> is the actual account name you log in with.

---

### Post by BSG Fan on 2011-07-31
> **CatKiller said:**
> No, it's /home/username

Okay, I found it. I deleted everything was there except the Sea Monkey I installed yesterday in absence of the old Firefox.
Do I also delete that folder of Sea Monkey or let it alone?

---

### Post by yetiman64 on 2011-07-31
> **BSG Fan said:**
> Okay, I found it. I deleted everything was there except the Sea Monkey I installed yesterday in absence of the old Firefox.
Do I also delete that folder of Sea Monkey or let it alone?

I'd suggest you leave it alone if it is separate to .mozilla.

---

### Post by BSG Fan on 2011-07-31
> **yetiman64 said:**
> I'd suggest you leave it alone if it is separate to .mozilla.

Okay, the Sea Monkey I talk was inside the .mozilla

thanks you to all you for the help.

I will re-install the Mozilla to see what going on

Hails!

:popcorn:

---

### Post by yetiman64 on 2011-07-31
OK I understand now, leaving .mozilla and deleting the 2 folders firefox and extensions within .mozilla (not sure if seamonkey uses extensions at all) should do fine.

---

### Post by BSG Fan on 2011-07-31
What is the best last Firefox version to download and that is stable and don't crash, etc, etc?

I am in this page:
[http://www.mozilla.com/en-US/firefox/channel/](http://www.mozilla.com/en-US/firefox/channel/)

What do you recommend and why?
1- Firefox Aurora
2- Firefox Beta
3- Firefox Beta (Guages)
4- Other?
5- What is the version 5? [http://en.wikipedia.org/wiki/Firefox#Version_5.0](http://en.wikipedia.org/wiki/Firefox#Version_5.0)

---

### Post by BSG Fan on 2011-07-31
Any recommendation?

---

### Post by mike555 on 2011-07-31
you don't download from their site , that's a Windows thing ... open your package manager ,type Firefox and check it to install....

---

### Post by Zachzee on 2011-07-31
Well another thing you might think about is there are a couple of other decent browsers (even though i use firefox also ).  I kind of like chromium it is like google chrome, i also have tried ones like Midori, Arora, Dooble and Rekonq. of these i would try chrome and arora. (if your firefox still has problems.)

---

### Post by rpaskudniak on 2011-07-31
BSG Fan,

I noticed that you were advised to delete the .mozilla directory from your home folder.  I would have suggested renaming it so you might be able to still recall out some add-ons you had.. well, added on.  Then, when your firefox problem is solved, you can put 'em back, one by one.  If it is in your trash folder, perhaps you can still recover it and rename it.

As to getting the latest version:

I'm not booted Ubuntu right now so it's hard to verify this.  But my instinct would be to:
[LIST]
[*]Click on [System]->[Synaptec Package Manager]
[*]Look for Firefox in the list.  I think you would right-click on that.
[*]Click on [Reinstall]
[/LIST]
It will download and reinstall the latest version available for your version of Ubuntu.

(I may have to retract this next time I boot Ubuntu. :guitar:   )

Good luck!

---

### Post by BSG Fan on 2011-07-31
**_All the users_** that helped me with my problem:

Thanks you!  The Firefox works now!

I solved the incident following all your ideas and opinions.

You all rock!

BSG Fan!

:popcorn:

---

