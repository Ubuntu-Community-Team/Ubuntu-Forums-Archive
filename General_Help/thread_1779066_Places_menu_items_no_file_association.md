---
title: "Places menu items no file association"
date: 2011-06-09
forum: General Help
---

### Post by micha8l on 2011-06-09
The following folders (or bookmarks) in my places menu will not open:* /Home Folder, /Desktop, /michael, /Videos, /Music, /Pictures, /Downloads* when I click them through this menu I'll get this error message: *Could not open location 'file:///home/michael/Desktop' No application is registered as handling this file. Picture: *[http://i898.photobucket.com/albums/ac183/micha8l/Screenshot.png](http://i898.photobucket.com/albums/ac183/micha8l/Screenshot.png)

I can access the folders mention through Nautilus without fault, so the issue seems to be segregated to the Menu Bar panel...

I've tried, without resolve, upgrading from 10.04  to 11.04, reinstalling ubuntu-desktop, compiz, and removing the Menu Bar panel and additing it again.

Any help would be appreciated, this is a really annoying one.

Regards,
Mike

---

### Post by yetiman64 on 2011-06-09
Try this (it is easily reversible if it doesn't work and will only affect your user not system wide for all users)

Open the file ~/.local/share/applications/mimeapps.list with the following command in terminal,

```
gedit ~/.local/share/applications/mimeapps.list
```Under the section > [Added Associations] add a new line with the contents, > inode/directory=nautilus-folder-handler.desktop; save the file and exit.

Try opening a folder in your places menu and let us know if it works.

---

### Post by micha8l on 2011-06-09
> **yetiman64 said:**
> Try this (it is easily reversible if it doesn't work and will only affect your user not system wide for all users)

Open the file ~/.local/share/applications/mimeapps.list with the following command in terminal,

```
gedit ~/.local/share/applications/mimeapps.list
```Under the section  add a new line with the contents,  save the file and exit.

Try opening a folder in your places menu and let us know if it works.

I did the following and it did not work for me, thanks for suggestion though.

This all started when I installed Samba

---

### Post by yetiman64 on 2011-06-09
1st delete the line you added in the previous attempt and save and exit the file.

OK if Samba is involved I would like to see all associations for directory opening in your system. Could you please post back the results of the following code?

```
cat /usr/share/applications/defaults.list /usr/share/applications/mimeinfo.cache ~/.local/share/applications/mimeapps.list ~/.local/share/applications/mimeinfo.cache | grep directory
``` this code checks the 4 files included and outputs the results in the terminal, copy and paste the terminal output here.

Or alternatively you could check the contents of the files in gedit and use the search function of gedit (search for inode, **Edit2**: or "directory" is better, without the quotes), and see if any files are missing the entry (all 4 of those files here contain an entry for "inode/directory=" on this install) I suspect one of these files has been modified incorrectly.

Edit: the 2 most important entries are the ones in /usr/share/applications. You may not have local entries but that is ok.

---

### Post by micha8l on 2011-06-09
Hey Yetiman, I ran your command and it outputted the following:

> inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
inode/directory=nautilus-folder-handler.desktop;
text/directory=evolution.desktop;
x-directory/gnome-default-handler=nautilus-folder-handler.desktop;
x-directory/normal=nautilus-folder-handler.desktop;

I'm no expert, but this is normal right?

kind Regards,
Mike

---

### Post by yetiman64 on 2011-06-09
> **micha8l said:**
> I'm no expert, but this is normal right?

Yes that does look normal, good. 

Will have to switch from my Lucid install to Natty here to check some compiz options that may be related to this after just noting a similar problem in another thread (will be back soon with an edit, use F5 to refresh your browser on this page occasionally :)) 

This may be related to the unity plugin or one of the other compiz plugins (I think you said in your 1st post about upgrading to 11.04. Is that what you're in now?)

Edit: no, I didn't find any settings that appear to be able to affect your situation. Check the directory entries in /usr/share/applications/defaults.list in particular (they will be already shown in the previous code along with other results) by navigating to the file and opening it with gedit (should open with gedit as read only by default). If they appear normal, I'm at a loss as to why the places menu isn't working. Will have to :-k some more about this thread. :)

---

### Post by micha8l on 2011-06-10
Thanks for your continued help Yetiman and yes I'm using 11.04.

I think you're right about it being related, to the Unity plugin; I've been having another issue, that I posted in a previous thread, were Compiz doesn't launch on login, I have to type 'compiz' into bash to get it started. However, I just typed 'unity' into bash and now all the links I mentioned earlier are indeed working, although I'd like to use Compiz as a windows manager.

Kind Regards,
Mike

---

### Post by mc4man on 2011-06-10
I might temporally set up a new user, log in and see if everything is ok there. If so then your issue is local.

You said that first started when setting up samba, that was on 10.10  and now on 11.04?

---

### Post by practic on 2011-06-10
...okay, I posted a reply but decided to remove it as I misread your problem. 

About a year ago I had a similar thing happen with the Places menu, but I can't remember now what I did to resolve it...Check to make sure "Open Folder" is the default handler for folders...and that it exists in /usr/share/applications. But if it works in Nautilus then this should be okay.

Barring a quick solution, you could do as suggested: create a new user. If it works there, it might be easier just to copy over your settings and delete your old account.

I would try rebooting a few times first though, in case it resolves itself.

---

### Post by micha8l on 2011-06-10
I installed Samba on Ubuntu 10.04 and then upgraded to 10.10 and then 11.04...

So I created a new user and thing are running well for him, not so much for me :p I wish I could have his account, but I don't know which files to copy over... there's so many hidden files I'm afraid I'll over-write something important. There's no easy solution here.

---

### Post by practic on 2011-06-10
> **micha8l said:**
> There's no easy solution here.

Yes, I know the feeling. 

To start, you can just copy over all your documents, music, videos, etc. No danger there. 

Then expose the hidden folders in your home dir and look for the obvious items: email, tasks, calendar, user photo, tomboy notes, browser favorites, fonts, themes, icons.

After that, it becomes more dangerous...you don't want to copy over the problem, so you can't safely copy over all the settings. I guess I would consider if there are any programs that I put a lot of work into setting up and configuring, and consider taking those things over. If you do it a bit at a time, and it breaks, you'll know where the problem was and be able to reverse it. Look in ".local", ".gnome2", and ".config" for anything that you may need...

---

### Post by kentfx on 2011-06-20
> **yetiman64 said:**
> Try this (it is easily reversible if it doesn't work and will only affect your user not system wide for all users)

Open the file ~/.local/share/applications/mimeapps.list with the following command in terminal,

```
gedit ~/.local/share/applications/mimeapps.list
```Under the section  add a new line with the contents,  save the file and exit.

Try opening a folder in your places menu and let us know if it works.


Just for the record -- that solved my problem.  Thank you.

---

### Post by yetiman64 on 2011-06-20
> **kentfx said:**
> Just for the record -- that solved my problem.  Thank you.

You're welcome. Glad it helped you :). The OPs problem is a bit more involved unfortunately. Cheers, yetiman64

<edit for OP removed just noted this is marked as solved>

---

### Post by ndstate on 2011-08-23
> **yetiman64 said:**
> Try this (it is easily reversible if it doesn't work and will only affect your user not system wide for all users)

Open the file ~/.local/share/applications/mimeapps.list with the following command in terminal,

```
gedit ~/.local/share/applications/mimeapps.list
```Under the section  add a new line with the contents,  save the file and exit.

Try opening a folder in your places menu and let us know if it works.

Worked for me.  Thanks so much!

---

### Post by drakulil on 2011-12-20
Hi this thing not work for me
> inode/directory=nautilus-folder-handler.desktop; 			 		

but this works

> inode/directory=nautilus.desktop; 			 		

---

