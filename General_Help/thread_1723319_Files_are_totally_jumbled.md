---
title: "Files are totally jumbled"
date: 2011-04-06
forum: General Help
---

### Post by Wuxin on 2011-04-06
[FONT=Times New Roman][SIZE=3]The file system on my computer has become completely confused and out of sync.  When I go into "documents," for example, I get the MPlayer for audio/video!  I go into "home file" and get an audio player for streaming FM!
Not every file is out of sync, but many are.

I believe this situation started a few weeks ago when I decided to install MPlayer.  I like MPlayer and especially its flexibility with regard to playing several kinds of media.  I downloaded MPlayer and tried to make it my "default" player; I think that may have been the problem.  Ever since then my files have been doing weird things and I'm unable to retrieve things (like documents) that I really need.  Any suggestions as to how I can begin to clean up this mess?  Thank you in advance!
[/SIZE][/FONT]

---

### Post by Krytarik on 2011-04-07
It seems like you have inadvertently set MPlayer as the default application to handle folders.

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by Wuxin on 2011-04-07
[FONT=Times New Roman][SIZE=3]It sounds like you know what you're talking about.  Unfortunately, I don't!  I'm kind of new at Ubuntu and I'm still finding my way with using terminals and executing the appropriate commands.  The link you kindly sent makes it sound like this is a problem of fairly long standing in Ubuntu.  Within that link there are links to several other links.  My impression is that this problem represents a flaw within Nautilus.  

My pragmatic question is what do I need to do to correct the situation!  It sounds like I don't need to do all that much, but it also sounds like it's a good idea to disable some other function to prevent this kind of thing from occurring again.  Thank you for your assistance with this!
[/SIZE][/FONT]

---

### Post by coffeecat on 2011-04-07
> **Wuxin said:**
> [FONT=Times New Roman][SIZE=3]
My pragmatic question is what do I need to do to correct the situation!
[/SIZE][/FONT]

Right-click on the desktop and choose "Create Folder". Don't bother to rename it anything special. Now right-click on the folder and choose "Open with other application". Make sure the "remember this application" tickbox is ticked. Scroll down the list and highlight "File Browser" Now click on "Open".

Problem solved. You can now delete the temporary folder on the desktop.

---

### Post by Wuxin on 2011-04-07
[FONT=Times New Roman][SIZE=3]Thank you much for your terse and complete instructions!  And indeed the files 
were restored to their rightful places.  

However, I'm not through yet.  I went into my "documents" file and tried to open a document I had stored there.  A box came up that read, "This link cannot be used because its target 'documents' doesn't exist."  And then below were two switches,
"cancel" and "move to trash."  So the files have been restored, but apparently I'm unable to gain access to the contents.  

What does this mean and how do I correct it?  But thanks again for helping me to get this far!
[/SIZE][/FONT]

---

### Post by coffeecat on 2011-04-07
This is a different problem.

First - your files were never out of sync and nor did they need restoring in the first place. All that had happened originally is that your had set folders to be opened with Mplayer, rather than the file browser. You had probably accidentally done what I described above but with Mplayer so the system remembered mplayer and tried to open it every time you wanted to open a folder. An easy mistake - easily corrected.

Now to your latest problem. 

> This link cannot be used because its target 'documents' doesn't exist.

This is not related to your original problem. You were trying to open a symlink to a document, not the document itself. A symlink is somewhat like a shortcut in Windows. The reason you are getting that error is that the document is not at the location the symlink is pointing to.

If the error message said "target 'Documents' " rather than "target 'documents' " then it sounds as though your Documents folder is missing. Linux is case sensitive, remember. Windows would treat 'documents' and 'Documents' as the same. They are different in Linux.

Did you delete the Documents folder? Have a look in your home folder. Is it still there?

---

### Post by Wuxin on 2011-04-07
[FONT=Times New Roman][SIZE=3]Interesting.  There are 2 folders in my Home File, one "documents," the other , "Documents."  In both there is one written document and there is an "x" in the lower right hand corner, and a closed padlock symbol in the upper right hand corner.  I don't remember either deleting a file or creating a new one.  Now neither wants to cooperate and produce the document![/SIZE][/FONT]

---

### Post by coffeecat on 2011-04-07
There is a 'Documents' folder set up as a default in Ubuntu. The folder 'documents' you must have created yourself, or a wayward app created it.

The x and padlock mean that the permissions and/or ownership are wrong, which is probably why it won't open. All files in your home folder and sub-folders should be owner by you. You can see what the permissions and ownership are by right-clicking on the file > Properties > Permissions tab. If the file is owned by root, it has no place being there.

Are the file names familiar to you?

---

### Post by Wuxin on 2011-04-07
[FONT=Times New Roman][SIZE=3]There are two permission names "john" and "John"!  I don't know what this means (again there is the "case" issue), but it seems two names are in place and that needs to be corrected.[/SIZE][/FONT]

---

### Post by coffeecat on 2011-04-07
> **Wuxin said:**
> [FONT=Times New Roman][SIZE=3]There are two permission names "john" and "John"!  I don't know what this means (again there is the "case" issue), but it seems two names are in place and that needs to be corrected.[/SIZE][/FONT]

Neither usernames nor group names have capitals, so I don't know where 'John' comes from. Is 'john' the name of your user account? Do you have an account called 'john' on your system?

The screenshot below is the permissions/properties window of a file on my desktop, but owned by root. This to give you some idea of what you should be looking at.

---

### Post by Wuxin on 2011-04-07
[FONT=Times New Roman][SIZE=3]So the idea, then, is that I need to have "root" in the place where it designates permission?  See, in a recent effort to correct this mess, a friend of mine had me renew my owner's account.  In order to do that I went into the large terminal (whole page) and basically reestablished password, identity, etc.  I guess the permission should have been granted to "root" but I didn't understand that at the time.  It may be that I now have *two* accounts at this point, thus causing the confusion.  (I don't think it was ever necessary, based on what you've said here, to create a new user's account.)  

But the deed is now done so how can I straighten this out so that I have permission once again to access my files?  Maybe I was wrong to install MPlayer and try to make it my default media player.  But unless you experiment and try different things, you can't learn and enjoy all that Linux
has to offer!  The nice thing about MPlayer, incidentally, is that it's capable of doing all kinds of things!  Thank you again!
[/SIZE][/FONT]

---

### Post by JKyleOKC on 2011-04-07
[FONT=Times New Roman][SIZE=3]> **Wuxin said:**
> So the idea, then, is that I need to have "root" in the place where it designates permission?  See, in a recent effort to correct this mess, a friend of mine had me renew my owner's account.  In order to do that I went into the large terminal (whole page) and basically reestablished password, identity, etc.  I guess the permission should have been granted to "root" but I didn't understand that at the time.  It may be that I now have *two* accounts at this point, thus causing the confusion.  (I don't think it was ever necessary, based on what you've said here, to create a new user's account.)Not quite!

The key fact here is that "john" and "John" are two totally different accounts. I suspect that when you "renewed" your owner's account, you actually created a brand new account that has the initial capital letter since most of us capitalize our names. If this is what happened, you now have two totally separate home directories, one for each account. If you log in as "john" you will see one of them, and if you log in as "John" you will see the other! One of them probably has your original files, and the other doesn't.

None of your files should show "root" in their permissions; the root user doesn't need permissions to go into any file -- and because of this one should never log in as root or use "sudo" except when making significant system changes that require modification of system files. Incidentally, only your original account will have the ability to use "sudo" and the near-duplicate one will not. That's automatic security at work. You can give the duplicate that ability, but it will be less confusing to go back to the original account and do everything there.

The case sensitivity built into all Linux systems is one of the major causes of confusion for newcomers, since it doesn't exist in Windows. However, after a little while most of us become used to it (and mostly avoid using uppercase in file or directory names, to stay out of trouble).

Hope this helps a bit...[/SIZE][/FONT]

---

### Post by Krytarik on 2011-04-07
Isn't it more like this? (See screenshot.)
It states both the username and the full name.

Also, check if there is indeed another user account:

[LIST]
[*]"System -> Administration -> Users and Groups"
[*]```
ls /home
```
[*]try to log in as the other "John"
[/LIST]
Greetings.

---

### Post by coffeecat on 2011-04-08
The thumbnail you posted looks fine. The krytarik- Krytarik is because "Krytarik" is what you typed for your name in the "who are you?" part of the installation, and the system suggested "krytarik" for your user account name, since account and group names must be all lower-case. In fact you could have changed both. What happened to john/John? Now I'm getting confused.

Also - what version of Ubuntu are you using, if indeed Ubuntu? Your permissions tab is laid out differently from the way it is in Lucid and Natty (and Maverick I think). In fact yours looks better.

Forget about root. I was just showing you a root-owned file in my user account because it sounded as though your problem might have been a root-owned file.

---

### Post by Krytarik on 2011-04-08
> **coffeecat said:**
> The krytarik- Krytarik is because "Krytarik" is what you typed for your name in the "who are you?" part of the installation, and the system suggested "krytarik" for your user account name, since account and group names must be all lower-case. In fact you could have changed both. What happened to john/John? Now I'm getting confused.Yeah,
- "krytarik" (lower case) is my username and
- "Krytarik" (upper case) is my full name

I guess the OP was referring to that.
> **coffeecat said:**
> 
Also - what version of Ubuntu are you using, if indeed Ubuntu? Your permissions tab is laid out differently from the way it is in Lucid and Natty (and Maverick I think). In fact yours looks better.
:p It's just Lucid, with the official Nautilus. But I chose the "advanced permissions" by enabling the Gconf key "/apps/nautilus/preferences/show_advanced_permissions". Those option is also included by Ubuntu Tweak.

---

### Post by coffeecat on 2011-04-08
> **Krytarik said:**
> 
I guess the OP was referring to that.


Sorry! I muddled you with the OP. #-o

:oops:

---

### Post by Wuxin on 2011-04-08
[SIZE=3][FONT=Times New Roman]Okay, now I am confused!  I checked the status of "ls /home" and received this message:

No command 'John' found, did you mean:
 Command 'john' from package 'john' (main)

So it appears from there this that there is only one account, and the lower case "john" is the established name.  So where do I go from here?  Basically I'm still trying to figure out how to gain access to my files.  I appreciate all the good input here--it's very instructive.  Yes, the business about "case sensitive" is important to note because I didn't think about when I used Windows and or Mac.  (Although I've heard there is some weird issue with case sensitivity in Mac, that may come to light in the future.)  

Is this issue something that can be resolved through GUI or is it simpler to use the terminal?  Let me know what is the easiest way to resolve this without resorting to too much technicality!   Thank you much!
[/FONT][/SIZE]

---

### Post by coffeecat on 2011-04-08
First, the command 'ls /home' would not give you the error message:

> **Wuxin said:**
> 
No command 'John' found, did you mean:
 Command 'john' from package 'john' (main)

You must have typed "John" in the terminal.

Second, I could give you a terminal command to change the ownership of all files in your home folder to yourself, but I'm not going to - yet - because I don't understand what you are trying to explain.

Earlier, you said there were two files with an x and padlock on their icons. Post a screenshot of the permissions tab as I did and then we can see what is going on.

---

### Post by JKyleOKC on 2011-04-08
[SIZE=3][FONT=Times New Roman]> **Wuxin said:**
> So where do I go from here?

Is this issue something that can be resolved through GUI or is it simpler to use the terminal?We may be able to cut through some of the confusion by trying both the CLI and GUI techniques. To verify the number of accounts, cut and paste this into the terminal:```
ls -la /home
```Then take a screen shot of the result and post it here. That will tell us the ownership and permissions of all the home directories. Next, do the same with  ```
less /etc/passwd
``` which will show all of the accounts in your system. Don't worry about revealing passwords; despite the name of the file, they're not in it.

As a final check, repeat the procedure with ```
cd
ls -l
``` which will list all the files and subdirectories in your home directory, together with their permissions and owner account names. The "cd" guarantees that you're in the home directory, and the terminal prompts will tell us the name of the account you're logged into.

To take a screen shot, simply press the "Print Screen" key and follow the prompts that will result.
[/FONT][/SIZE]

---

### Post by Wuxin on 2011-04-09
How do I take a screen shot of just the terminal panel?  One option says you can limit the area to be copied, but I don't know how to do this.  Sorry!

---

### Post by JKyleOKC on 2011-04-09
On my system, it's hold down the ALT key while pressing PrintScreen. I believe it's the same for the other window managers but am not certain of that. Here, this brings up a dialog asking where to save the shot to; I just accept its suggestions and click "save" then upload the saved file as an attachment to the forum message by clicking the "Manage Attachments" button on the reply page, down under "Additional Options."

---

### Post by Krytarik on 2011-04-09
> **Wuxin said:**
> How do I take a screen shot of just the terminal panel?  One option says you can limit the area to be copied, but I don't know how to do this.  Sorry!
You can also just copy its content and post it in code-tags, by using the #-button in the editor.

---

### Post by Wuxin on 2011-04-10
[FONT=Times New Roman][SIZE=3]The dialogue box I receive doesn't have anything about transferring screen shots to online entries.  The options are such fixed things as "documents," "desktop," etc.  How do I take a screen shot of just the terminal in question and transfer that to a reply box?  I know there must be a way because I've seen people  do it.  Thanks again![/SIZE][/FONT]

---

### Post by Krytarik on 2011-04-10
There is really no reason to do actual screenshots of your terminal window, because everything in it is text. You can simply highlight the relevant text, copy it via the menu, and paste it into the forums editor, then click at the #-button to enclose it by code-tags.

---

### Post by JKyleOKC on 2011-04-10
> **Wuxin said:**
> [FONT=Times New Roman][SIZE=3]The dialogue box I receive doesn't have anything about transferring screen shots to online entries.  The options are such fixed things as "documents," "desktop," etc.  How do I take a screen shot of just the terminal in question and transfer that to a reply box?  I know there must be a way because I've seen people  do it.  Thanks again![/SIZE][/FONT]That's the dialog asking where to save the screen shot. I just take note of the location that it suggests, and click the "save" button. To get just the terminal window, first click the title bar of the terminal window to make sure that it has the focus, then press and hold either ALT key while presing and releasing PrintScreen. That brings up the save dialog.

The reason I suggest screen shots is that copying and pasting from the terminal window is slightly different from the usual ways of doing it. The Ctrl-C keystroke used for "copy" in editor programs has a different meaning in the terminal, so it's necessary to use shift-ctrl-C instead. However if this doesn't pose a problem, Krytarik's suggestion will work equally well -- and will actually be more readable here on the forum since screen shots are always reduced!

---

### Post by Vaphell on 2011-04-10
also in linux you can copy paste by highlighting-middleclicking. It's even better than ctrl-c, ctrl-v combo, because you can do that in lazy mode with no hands on keyboard :)
Highlight the output of given commands, DON'T deselect, switch focus to browser, middle click in text input area, voila.

---

### Post by Wuxin on 2011-04-10
[SIZE=3][FONT=Times New Roman][/FONT][/SIZE][SIZE=3][FONT=Times New Roman]After copying and pasting all that info I received the following message!  

[/FONT][/SIZE]You have included 23 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again. 

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

[FONT=Times New Roman][SIZE=3]So they won't let me include all that information in those boxes.  What is another way to proceed?  Remember, I'm trying to gain access to folders which have "padlocks" and "X's" on them.  Thanks so much![/SIZE][/FONT]

---

### Post by JKyleOKC on 2011-04-10
Try this from a terminal window, but be very cautious about what you do because it's akin to handling a tommy gun with the safety disengaged (been there, done that, some 60 years ago -- and nearly paid for it with my life)...

```
gksu nautilus
```

You should be able to access those folders from the resulting file manager window, but don't try to change anything. Just verify that you have access. If this works for you, we can then tell you exactly what to change and how to change it.

EDIT: To overcome that limit on the number of images, try doing just one result per message and post several messages. This message editor converts some character combinations to smileys and that might be running the count up!

---

### Post by Wuxin on 2011-04-15
[FONT=Times New Roman][SIZE=3][COLOR=black]Okay, I'm back with this...I was out of town for a few days.  The problem persists:
when I click on "Documents" and "Home Folder" under places--I get MPlayer!  Under Home Folder I get an FM streamed station and under Documents I get the
MPlayer GUI.  Somehow I have to get a command in the terminal that will get MPlayer out of the "Home Folder."  In fact it has *replaced* the Home Folder!  I don't know how this came about, but I want to do whatever it takes to fix it.  
[/COLOR][/SIZE][/FONT]

---

### Post by Vaphell on 2011-04-15
find any directory (if there is none available create it on desktop), rightclick, open with..., select file browser, make sure 'remember this program...' checkbox is ticked, apply

---

### Post by Wuxin on 2011-04-16
[FONT=Times New Roman][SIZE=3]Sorry, I don't follow you...when I right click on the desktop I see "create folder,"
"create document," but nothing about creating a directory.  How do you bring this about and what does it accomplish?  Thanks!
[/SIZE][/FONT]

---

### Post by oldos2er on 2011-04-16
"Folder" and "directory" refer to the same thing, so click 'Create folder'.

---

### Post by Wuxin on 2011-04-16
[FONT=Times New Roman][SIZE=3]Okay, I have done that.  Now what to do from here?  (Do I need to 
save that folder, or can I send it to trash?)
[/SIZE][/FONT]

---

### Post by oldos2er on 2011-04-16
If you followed the steps in Vaphell's post and everything's working correctly, I think it's safe to delete the folder you created.

---

### Post by Wuxin on 2011-04-16
[FONT=Times New Roman][SIZE=3]Okay, when I click on Home Folder, I now see the list of folders stored there.  Well and good. But I am still unable to open my documents folder: it has a "padlock  and a check" by it.  That's what I need to find out how to undo at this point.  Thanks everyone for your continuing good efforts on this--I do appreciate it![/SIZE][/FONT]

---

### Post by oldos2er on 2011-04-17
Sounds like some permissions were changed on your documents folder. Open a terminal and run ```
sudo chown user:user -R /home/user/Documents
``` replace "user" with your user name.

---

### Post by Wuxin on 2011-04-18
[FONT=Times New Roman][SIZE=3]Okay, I'm going to try the above command momentarily, but here is what a Linux friend suggested to me and what he urged me to ask here:

It appears that Nautilus has gone to hell on me for reasons unknown.  What this guy said I need to find out is how to delete and recreate the default Ubuntu user (me, in this case) to get that trashed Nautilus stuff out of the way.  That might clear up this whole mess.  Does anyone know how to do this?  Thanks again!

[/SIZE][/FONT]

---

### Post by Wuxin on 2011-04-18
Sounds like some permissions were changed on your documents folder. Open a terminal and run      Code:
     sudo chown user:user -R /home/user/Documents 
 replace "user" with your user name.

[SIZE=3][FONT=Times New Roman]No go.  I tried the above and got the following reply: invalid user: 'user: [name]'
Again, I think my friend's suggestion is what I need to do here--delete and recreate the default Ubuntu user.  For some reason my user status is not recognized.
[/FONT][/SIZE]

---

### Post by oldos2er on 2011-04-18
What is the result of **ls /home** ?

---

### Post by JKyleOKC on 2011-04-18
> **Wuxin said:**
> Sounds like some permissions were changed on your documents folder. Open a terminal and run      Code:
     sudo chown user:user -R /home/user/Documents 
 replace "user" with your user name.

[SIZE=3][FONT=Times New Roman]No go.  I tried the above and got the following reply: invalid user: 'user: [name]'
Again, I think my friend's suggestion is what I need to do here--delete and recreate the default Ubuntu user.  For some reason my user status is not recognized.
[/FONT][/SIZE]If you do that, you'll probably lose your ability to use sudo and with it the ability to continue trying to fix the problem!

There are some hidden files in your home directory that set up the association between file types and double-clicking actions. If you ever used the "Open with..." feature in Windows, and saw the "Always open" checkbox that set up the association, this is the very same functionality implemented in Ubuntu. Apparently part of your problem is that those files got mixed up, and in attempting to solve that, you got a permissions mismatch on your Documents (note the upper case!) folder.

In a terminal, use the command "cat /etc/passwd" and look at the result. Near the bottom of the list you should see a line similar to ```
jk:x:1000:1000:Jim Kyle,,,:/home/jk:/bin/bash

```but with YOUR user name in place of "jk" and your own name in place of mine. The two numbers "1000" are my UID and GID, respectively, and yours should also be 1000 since that's where Ubuntu starts assigning ID numbers. If they are something different, that's the source of your permissions problem.

If you delete your user and create a new one, you will get higher numbers, and will lose access to all of your files even if you give the new user the same name. What's needed is to determine what UID is in the directories for your critical files, and then use "sudo chown" to make them match the one you see in the "passwd" listing.

To do this, make sure you are in your home directory, then use the terminal command "ls -la * >mylist.txt" to get a list of everything (it will be much longer than you expect) that you can then inspect with a text editor. The 3rd and 4th columns of this list will show the owner and group associated with each file; if it shows your user name there all should be well, but if it shows a number that indicates the file is owned by a user that no longer exists in the system, and if it shows "root root" then it was probably created using "sudo" and needs to be changed via the "chown" command.

Incidentally, despite its name, the passwd file does NOT have your password in it -- that's stored elsewhere, and the "x" in my example is where it was in the very first versions of Linux!

EDIT: When you tried the chown and got an error, I suspect that you misinterpreted part of the command. If your user name is "wuxin" then it should have been "sudo chown wuxin:wuxin -R /home/wuxin/Documents" instead of "user:wuxin" -- it's an easy mistake to make when you don't yet know that the ":" is often used as a separator in Linux! Try it again and see if that doesn't make a difference!

---

### Post by Wuxin on 2011-04-18
[FONT=Times New Roman][SIZE=3]Thanks for your detailed reply.  [/SIZE][/FONT]

In a terminal, use the command "cat /etc/passwd" and look at the result. Near the bottom of the list you should see a line similar to      Code:
     jk:x:1000:1000:Jim Kyle,,,:/home/jk:/bin/bash 
but with YOUR user name in place of "jk" and your own name in place of mine. The two numbers "1000" are my UID and GID, respectively, and yours should also be 1000 since that's where Ubuntu starts assigning ID numbers. If they are something different, that's the source of your permissions problem.

[FONT=Times New Roman][SIZE=3]Okay, this seems to check out fine.  And the "1000" number is in place.  So far so good!  Now,

[/SIZE][/FONT]To do this, make sure you are in your home directory, then use the terminal command "ls -la * >mylist.txt" to get a list of everything (it will be much longer than you expect) that you can then inspect with a text editor. The 3rd and 4th columns of this list will show the owner and group associated with each file; if it shows your user name there all should be well, but if it shows a number that indicates the file is owned by a user that no longer exists in the system, and if it shows "root root" then it was probably created using "sudo" and needs to be changed via the "chown" command.

[FONT=Times New Roman][SIZE=3]I got nothing when I typed in this command.  [/SIZE][/FONT]

ls -la * >mylist.txt

[FONT=Times New Roman][SIZE=3]I did get something when I typed *ls -la* but not the wholes script.  What would that indicate?  Where is the home directory?  Is this command supposed to be typed in a terminal or somewhere else?...This isn't clear to me.  Thanks again for support.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]

---

### Post by Wuxin on 2011-04-18
[FONT=Times New Roman][SIZE=3]Wait!  I did discover something...There is a file called *mylist.txt* in the home folder.  Is this what I'm looking for?  Now what do I look for with it?[/SIZE][/FONT]

---

### Post by JKyleOKC on 2011-04-18
Yep, that's the file. Just open it up with a text editor. It will be a detailed listing of your home directory, plus all of its subdirectories one level down. You'll be looking for any line that has "root root" instead of your user name in columns 3 and 4, or a number such as 1001 there instead.

Here's what the columns mean: The first is the permissions list; if it starts with "d" the line is a directory, while "-" means a file. The next three letters are the owner permissions, followed by group and finally by "everyone else." The second column is the number of links associated with the entry; you can ignore it at this point. Third is the owner, fourth is the group, fifth is the size in bytes, fifth the last modification time, and finally the filename.

---

### Post by Wuxin on 2011-04-18
[FONT=Times New Roman][SIZE=3]What does that mean to "open it with a text editor"?  Is this something I do in a terminal, or can I simply open that file in the home directory?  Forgive me, but I'm still new to a lot of this terminology!  Thanks![/SIZE][/FONT]

---

### Post by Wuxin on 2011-04-18
[FONT=Times New Roman][SIZE=3]Is this what I'm looking for?  Now what does this tell me?  How do I move from this to being able to get into my files?  Thank you again.  [/SIZE][/FONT]




-rwxr-xr-x 1 john john      293 2010-11-09 21:24 checkbox-gtk.desktop
lrwxrwxrwx 1 john john        9 2011-04-04 11:08 documents -> Documents
-rw-r--r-- 1 john john      179 2010-10-18 17:32 examples.desktop
lrwxrwxrwx 1 john john       39 2010-11-09 21:31 Link to checkbox-gtk.desktop -> /home/john/Desktop/checkbox-gtk.desktop
-rw-r--r-- 1 john john        0 2011-04-18 20:14 mylist.txt
-rw-r--r-- 1 john john   280408 2008-02-10 15:46 ppc-codecs_20071007-0medibuntu1_powerpc.deb
-rw-r--r-- 1 john john    75033 2010-11-07 22:46 troubleshoot.txt
-rw-r--r-- 1 john john 14284826 2009-03-29 11:37 w32codecs_20071007-0medibuntu2.1_i386.deb
-rw-r--r-- 1 john john   209974 2008-04-27 16:00 w64codecs_20071007-0medibuntu1_amd64.deb
-rw-r--r-- 1 john john  1891684 2011-03-28 17:50 wfmu.mp3

Desktop:
total 52
drwxr-xr-x  3 john john  4096 2011-04-18 00:21 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..
drwx------  3 john john  4096 2011-04-16 11:18 Panikkar Stuff
-rw-r--r--  1 john john 18982 2011-04-04 08:28 Traffic court.odt

Documents:
total 24
drwxr-xr-x  2 john john  4096 2011-04-16 18:01 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..
lrwxrwxrwx  1 john john     9 2011-04-04 11:08 Documents -> Documents

Downloads:
total 32
drwxr-xr-x  2 john john  4096 2011-04-16 22:10 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..
-rw-r--r--  1 john john  1905 2010-11-16 08:14 medibuntu-key.gpg

Music:
total 20
drwxr-xr-x  2 john john  4096 2010-10-19 02:40 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..

Pictures:
total 20
drwxr-xr-x  2 john john  4096 2010-10-19 02:40 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..

Public:
total 20
drwxr-xr-x  2 john john  4096 2010-10-19 02:40 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..

Templates:
total 20
drwxr-xr-x  2 john john  4096 2010-10-19 02:40 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..

Videos:
total 20
drwxr-xr-x  2 john john  4096 2010-10-19 02:40 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..

---

### Post by JKyleOKC on 2011-04-18
Here's the essential part of that list: ```
Documents:
total 24
drwxr-xr-x 2 john john 4096 2011-04-16 18:01 .
drwx------ 54 john john 16384 2011-04-18 20:07 ..
lrwxrwxrwx 1 john john 9 2011-04-04 11:08 Documents -> Documents

```This says that you have a total of 24 files and directories in the Documents folder, including the two "navigation" entries named . and .., but only lists three of them. That third line shows that "Documents" is a link, but pointing to itself -- which should not ever be the case. This is causing the system to "chase its tail" and that apparently causes things to stop right there, which would explain your inability to find your files.

While I've been doing system programming for more than 40 years, and in Linux for at least 10, I've never run into this exact situation before. I really don't know what you should do next to get rid of that link without losing all access to your document files, so the best thing to do is just nothing at all until we can get a file system guru into the thread to tell us how to remove the link without removing the entire Documents directory!

I'll see if I can find someone to help us with this. I'm fairly certain that things will return to normal if we can get that link corrected or removed.

EDIT: I created a test folder in my own system and built a similar link into it after creating a few files, but the link did NOT prevent the other files from showing up in the result of a "ls" command. This means that your documents MAY have been deleted in the same time period that the link got created. Have you looked in the "trash" bin to see if they may have been moved there? I'll still be looking for a guru to help here, but I'm now less optimistic than I was a few minutes ago...

---

### Post by Wuxin on 2011-04-19
[FONT=Times New Roman][SIZE=3]Thanks for your continued good efforts to help me solve this problem.  I don't quite know what to say...I'm honored that I've come up with a problem that's stumped an expert programmer??  What did I do to bring this about?  Is it a bug of some kind within the Linux os?  One silver lining in this dark cloud is that I am still able to work on the computer--Linux is obviously a stable program.   Fortunately I don't have a lot of documents saved on my laptop so it wouldn't be an extraordinary loss.  

Until this is resolved, where should I store text files written on my computer?
[/SIZE][/FONT]

---

### Post by JKyleOKC on 2011-04-19
You can create a new folder in your home directory; I had to do this on a Win98 system some time ago and the same approach will work in Linux: from a terminal, enter "mkdir MyDocs" to create a folder named "MyDocs" and then store your documents in it rather than in the existing Documents folder. You'll have to remember to include the folder name, or navigate to it, when saving the files, since there won't be any automatic routing to it.

You might be able to keep using the Documents folder; my little test here showed that the link did NOT block access to files in the folder. I'm beginning to suspect that something went wrong when you did the original restoring, so that they did not ever make it into the folder to begin with. We'll probably never know for sure, though...

---

### Post by coffeecat on 2011-04-19
> **Wuxin said:**
> [FONT=Times New Roman][SIZE=3]  What did I do to bring this about?  Is it a bug of some kind within the Linux os? 
[/SIZE][/FONT]

I don't think it's a bug because I think I've reproduced what you are seeing. I've managed to create a symlink (with some fiddling around) called "Documents" inside my Documents folder, linking back to itself. That is, linking back to the link, not the Documents folder. Except that it is a broken link. When I do 'ls -la' inside my Documents folder, I get:

```
total 40
drwxr-xr-x  2 richard richard  4096 2011-04-19 13:41 .
drwxr-xr-x 55 richard richard  4096 2011-04-19 13:14 ..
lrwxrwxrwx  1 richard richard     9 2011-04-19 13:41 [COLOR=Red]Documents[/COLOR] -> [COLOR=Red]Documents[/COLOR]
-rw-r--r--  1 richard richard 29972 2011-03-30 18:12 Final2.pdf
```... with the word "Documents" appearing in red, as I've shown. Do you get that - the word Documents showing in red?

Also - the thumbnail below is a screenshot of the Documents folder. You can see that I'm getting the x and the padlock on the broken Documents symlink - similar to what you described earlier. Is this what you are seeing?

---

### Post by Wuxin on 2011-04-19
[FONT=Times New Roman][SIZE=3]Okay, I think I may have resolved this thing.  Not that I recovered the documents, I didn't, but I think I won't be having further difficulties.  Last night--late--a friend wrote me and advised me to try this:

[/SIZE][/FONT]rm -rf Documents
  mkdir Documents

[FONT=Times New Roman][SIZE=3]I did and it seems to have cleared the Documents file of obstruction, but whatever was there (if anything) is gone.  And he mentioned something about "symlink" (what is this?).  Apparently this is a bug that's been recognized since 2007 but people seldom run into it because very few people create that "symlink" situation.  

Can someone explain what this means (symlink) and what I did to create this mess?  I just want a sense of what *not* to do so that I won't stumble into this in the future.  Thank you one and all for excellent analytical skills and service above and beyond the call of duty!  I can see why people love Ubuntu and other Linux distros!
[/SIZE][/FONT]

---

### Post by JKyleOKC on 2011-04-19
A symlink is somewhat like a Windows shortcut; it's a way of making one filename (or directory name) point to another file or directory. The bug mentioned as having been around since 2007 is simply that it's possible to create a symlink that points to itself, which should never be allowed to happen. However I don't know of any way that such a symlink could be created without issuing an explicit command to do so, and it's not a command that's likely to be entered by mistake.

I still suspect that the real problem happened when you first attempted to restore the files, but we'll never know for sure. At least your system should now be back in good running order.

---

### Post by Thewhistlingwind on 2011-04-20
You could always try a file recovery program to see if your documents got pwned by your symlink mess and yet still haven't been written over. Though if the documents weren't that important, I'd advise against it, those utilities can cause way more harm then help for a lot of cases. (And can potentially break your system further.)

---

### Post by Wuxin on 2011-04-20
[FONT=Times New Roman][SIZE=3]Yes, I suspect you are correct...trying a file recovery program might do more harm than good!  At least the thing is working now and it's probably best to leave well enough alone.  Again, thank you everyone for the wonderful assistance and truly expert advice!  

This is a very supportive community--compare this with "customer-no-service" that you get when dialing 800 phone numbers for Windows and related products!  The likelihood of getting someone knowledgeable on the phone is next to nil!
[/SIZE][/FONT]

---

