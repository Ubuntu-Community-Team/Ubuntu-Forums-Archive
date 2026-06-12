---
title: "Administrative task"
date: 2009-08-18
forum: General Help
---

### Post by kasey23 on 2009-08-18
Hey all,

I'm new to ubuntu and linux in general. I made a stupid mistake and was wondering if someone could help me fix it. I've googled it and couldn't find a solution. I just installed ubuntu a few days ago and been poking around quite a bit. I went to system, administration and users and groups. I don't have the root account enabled. Under my account I disabled administrative tasks to see what would happen and now I can't get into users and groups to change it back. Like I said I've googled this problem and can't find a solution. Please Help!!!!:confused:

---

### Post by HiImTye on 2009-08-18
ouch. sounds like you'll need to reinstall if you don't have any account that can perform administrative tasks

---

### Post by kasey23 on 2009-08-18
Hey, thanks so much for the reply:)!!!!! So there's no way around reinstalling? Not that it's a big deal to me....I was just hoping there was a more complex way of doing it.....to get my feet wet so to speak.:)

---

### Post by Grenage on 2009-08-18
There will be a way, definitely.  Unfortunately I have never had to do it, so I am unsure how.

---

### Post by HiImTye on 2009-08-18
unfortunately not, you need administrative access to enable an administrative account. caught yourself into sort of a catch-22 lol

---

### Post by aesis05401 on 2009-08-18
No wait, hold on.  This is easy.  Let me just double check my method before posting.  No reinstall necessary if you have access to grub menu on boot.

Brb.. opening VM to check this real quick.

---

### Post by MichealH on 2009-08-18
Should'nt this be in Beginner Help/Advice Section? But glad to know that you are getting to know linux hopefully youwill get to our stage We were once all abseloubte beginners

---

### Post by aesis05401 on 2009-08-18
Yeah, easy.  On boot the screen will say 'Loading grub...press escape to enter boot menu..' or something like that.  Hit the escape key and you will see a simple menu with different Linux versions listed.

Select your Linux kernel using the arrow keys (the one with the highest version number is probably the one you want).  With the proper kernel highlighted hit the 'e' key.  

You will see another similar menu, highlight the 'kernel' line and hit 'e' key again.  Now you will have a line that ends in something like 'ro quiet splash' or some variation - delete this end section and anything that follows on the line.  Now add 'rw init=/bin/bash' to the end of the line (without quote marks).  Press enter and then hit the 'b' key to begin booting with your customized boot command.

When you get your root prompt type:
```

nano /etc/group

```

Add yourself to any group you want by adding your user name to the end of the right line.  Separate user names with a comma, but no space - example:
```
users:x:27:aesis,drone
``` would add me and the user named drone to the users group.  

Save with ctrl+o, exit with ctrl+x, sync, reboot -f, your machine will reboot as normal.  You should be home free at this point, but post back just in case it doesn't work.

---

### Post by kasey23 on 2009-08-18
Thank you everyone for your replies:P

aesis05401 thank you for all the work!! Okay so how do I get to the root prompt?

---

### Post by aesis05401 on 2009-08-18
This is not the same type of root prompt as enabling root login.  I do not know all the differences, but there is not host information loaded, none of the expected environment variables, etc.. Think of this method almost like booting from a utility cd that allows us to use just enough tools for the task ;)

The steps are listed in my last post.  The changes you make to the grub command are temporary, so when you reboot you will be back to the normal boot routine.

---

### Post by kasey23 on 2009-08-18
Okay sounds good. What I meant was in the steps you listed in your post you wrote "When you get your root prompt type:" and I was wondering does this automatically open up or do I have to open it up myself and if so how??:)

---

### Post by aesis05401 on 2009-08-18
The prompt is what  you will see shortly after pressing the 'b' key.  The machine will flash some brief boot messages to the screen then you will see the prompt.

Issue the commands listed in my post to edit the /etc/group text file.  Once you have the file open it will be pretty straightforward.  Use your arrow keys to move to the group you want, add your name to the end of the line, save, exit...

The sync command is just to make sure you are cleaned up, and then reboot -f should reboot your machine.  When you come back up, log in as normal and see if your permissions are restored.

Good luck, I have to log out for the night.

---

### Post by aesis05401 on 2009-08-18
Yikes.. the command is 'sync' not 'synch' ... I am editing the earlier posts now ;)

P.S. I think you need to be added to group 'adm'

---

### Post by kasey23 on 2009-08-18
:) I'm going to get started on this tomorrow. I'll post to let you know how it went:)

Thanks again.

---

### Post by kasey23 on 2009-08-18
Okay I got to the part where I add my user name. My username is already beside admin so I added to root aswell. but then when I go to save changes or exit I get this...
 
File Name to Write: /etc/group
 
Not sure what to type here???:)

---

### Post by aesis05401 on 2009-08-18
> **kasey23 said:**
> Okay I got to the part where I add my user name. My username is already beside admin so I added to root aswell. but then when I go to save changes or exit I get this...
 
File Name to Write: /etc/group
 
Not sure what to type here???:)

Yes, /etc/group is the name of the file as we would like it to be saved, so just hit enter there.  

You should not be in group root, though.  'adm' is the group you want to join to restore your 'first user' sudo powers on an Ubuntu system.

---

### Post by dtoronto on 2009-08-18
You can remount the hard drive to another Linux install and edit your admin config files that way too.

---

### Post by aesis05401 on 2009-08-18
> **dtoronto said:**
> You can remount the hard drive to another Linux install and edit your admin config files that way too.

I realize now that I should have given some sort of gui based instructions for doing this... It just made more sense to me using command line.

---

### Post by kasey23 on 2009-08-19
Hey guys thanks for the replies, I would've gotten back sooner but haven't been able to get to the computer.
 
aesis05401 I do hit enter, but then I get another root prompt. i tried saving, exiting but I just end up at the root prompt again. I looked and I'm already added to admin, that's why I added myself to root, i don't know if that will do anything.
 
dtoronto thank you for the advice but I don't know how to do that. If you are willing to give me some more info about it I would like to give it a try aswell:)

---

### Post by aesis05401 on 2009-08-19
Ok, at the second prompt is when you type ```

sync
reboot -f

```

But I have a concern.  'admin' and 'adm' are two different groups.  'adm' is a special group only for the 'first user' account which gets special privileges on Ubuntu. 

When you say you are added to admin, does this include the 'adm' group?

---

### Post by aesis05401 on 2009-08-19
Hello again, 

I realize my instructions should have been presented more concisely.  
I'm going to repost the command line instructions step by step just to
practice giving better advice.  I am just using the code box for
appearances.

How to recover first user rights using the grub bootloader and the
command line:
```

**Reboot computer and enter grub boot menu by pressing '[B]esc**' during boot[/B]
   - You should now be seeing a simple menu listing linux installations

**Select the linux installation to modify and press '[B]e**' key[/B]
   - You should now be seeing a list of specific parts of the boot
sequence for the selected linux installation.

**Select the 'kernel' line and press '[B]e**' again[/B]
   - You should now be seeing a line of text that sets kernel boot
options.  Any changes we make here will be discarded upon reboot unless
you explicitly save the options, but we will not be doing that.

[B]Replace the existing boot options beginning with 'ro' and all the way
to the end of the line.  Enter your replacement options: **rw init=/bin/bash**[/B]

**Press 'enter'**
   - You are now back to the previous menu.  Leave 'kernel' highlighted.

**Press 'b' key**
   - Your machine will now begin the boot process. You will know you are
booted when you see the root prompt. 

[B]From the root prompt: Launch command line text editor named 'nano' and
load the /etc/group text file: **nano /etc/group**[/B]
   - The screen you are seeing is a full featured command line text
editor, and it should be displaying the contents of the /etc/group text
file.

**Use arrow keys to locate the 'adm' line item.**  
   - This is the line where we want your user name to be placed to gain
the 'first user' special privileges.

**Add your user name to the end of the 'adm' line**.  
   - Do not allow any space characters between the ':' at the end of the
'adm' line and your user name.
   - Add your user name to any other line you need at this time.  If
there is already another user name on the line, simply add your user
name to the line with a comma, and without a space: 'aesis,drone,pete'
would assign the three user names listed to the group defined at the
beginning of the line. 

**Tell nano to save the file: [B]ctrl+o**[/B]

**Press 'enter' key when nano asks the 'File Name to Write**' 
   - this will cause the changes to overwrite the existing /etc/group
with your updated group assignments.

**Exit nano and return to the root prompt: [B]ctrl+x**[/B]

**Clean up anything hanging around in the buffers by typing '[B]sync**'
and pressing '**enter**' key.[/B]

**Reboot machine by typing: [B]reboot -f**[/B]

```

When you reboot you should have your privileges restored.

---

