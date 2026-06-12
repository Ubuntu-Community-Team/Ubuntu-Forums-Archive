---
title: "Uh-oh! I did a very silly thing"
date: 2010-02-24
forum: General Help
---

### Post by Wibb-untu on 2010-02-24
Hello everyone

I have a serious problem, and could really do with some help!

Having little clue as to what I was doing, I attempted to try and move all the files from the current directory to the directory just under it. I tried this command:

[COLOR="Red"]Warning - do NOT try this!!!![/COLOR]
sudo mv /* ..

To my horror and amazement, this is what I got:

[FONT="Courier New"]$ sudo mv /* ..
mv: cannot move `/boot' to `../boot': Device or resource busy
mv: cannot move `/dev' to `../dev': Device or resource busy
mv: cannot move `/lib' to `../lib': Directory not empty
mv: cannot move `/proc' to `../proc': Device or resource busy
mv: cannot move `/sys' to `../sys': Device or resource busy
mv: cannot move `/var' to a subdirectory of itself, `../var'[/FONT]

... thank god those ones didn't get moved, but unfortunately at least /usr and /bin were moved ... somewhere else. I have no idea where. I don't even know what the command actually did.

Can anyone tell me if the /usr and /bin directories are lost forever in the magical land of ".."? Is there a way to rescue them? I daren't lose my connection in case I can never get back on again.

:(

---

### Post by ndefontenay on 2010-02-24
Hi.

Since you've tried to move /* to .. that means you've tried to move anything located in / one above / which is kind of impossible.

From what I see in the error message the command try to move all folders to themselves like /root to /root.

Can you try find -name usr? (man find to see if there's an option to look only for folders)

Nico

---

### Post by Wibb-untu on 2010-02-24
I am a bit limited in regards to what I can do :( I seem to still be able to mv and cd, but most commands only get me this:

[FONT="Courier New"]/$ find -name usr
/$ man find
-bash: /usr/bin/man: No such file or directory
/$ ls -la
-bash: /bin/ls: No such file or directory[/FONT]

find did not do anything, it just sat there

---

### Post by ndefontenay on 2010-02-24
What I don't understand is why usr could move when everything else was failing with the error that it can't move to itself.

If that's the case why this one could move. It's beyond me.
We are missing something here.

if you are still in the current directory, can you try 
cd ../usr?

this was the destination of your previous mv. So in theory whereever that is you should be able to get there.

I don't know what else to try, it's going to be quite tough to know what's where because ls is not working too.

---

### Post by Wibb-untu on 2010-02-24
ok, I found the root directories - I was in /var/lib/svn/ at the time.

/bin had been moved to /var/lib/svn/bin
I realised because /var could not be moved into a subdirectory of itself

So if I did this:
cd /var/lib/svn
mv bin/* /

sudo doesn't work anymore so perhaps it won't do anything.

Will that restore root directories back to the root? I can fix my svn repositories later.

---

### Post by bruno9779 on 2010-02-24
Back up and reinstall.

---

### Post by nothingspecial on 2010-02-24
I just tried this on my testing machine and couldn`t do it. Are you sure you have the syntax exactly right.

---

### Post by Arand on 2010-02-24
Since the system itself seems to be at a rather messy state at the moment, it might be an idea to use a liveCD to do the moving-back, if you know what needs moving that is.
- Arand

---

### Post by nothingspecial on 2010-02-24
Sorry, I thought you were in / , didn`t see the replies while testing this.

I did a similar thing last week just to see if I could recover. I moved every file on the entire partition to /

I couldn`t recover. You could try and move everything back though in this case.

---

### Post by Wibb-untu on 2010-02-24
Basically I had exported a repository into a new folder, entered the folder and wanted to move everything from /trunk into the folder below it. I got the command completely wrong as you can see and it's the first time I have done something as disastrous as this.

[FONT="Courier New"]me@dev:/var/lib/svn/magento-1.3.2.4-modified/trunk$ sudo mv /* ..
mv: cannot move `/boot' to `../boot': Device or resource busy
mv: cannot move `/dev' to `../dev': Device or resource busy
mv: cannot move `/lib' to `../lib': Directory not empty
mv: cannot move `/proc' to `../proc': Device or resource busy
mv: cannot move `/sys' to `../sys': Device or resource busy
mv: cannot move `/var' to a subdirectory of itself, `../var'[/FONT]

Perhaps it's a lesson to be learned... avoid using sudo as much as possible!

---

### Post by nothingspecial on 2010-02-24
I still don`t understand why you could do it and I couldn`t.

---

### Post by ajgreeny on 2010-02-24
Try starting in recovery mode from the grub menu, which will give you root permissions.  You may then be able to use cp (copy) commands rather than mv (move) which may be safer, to copy everything that did move back to /root, where it should be.

To check where everything is at the moment, it may be worth trying ```
updatedb
``` from recovery mode as well, which will update the database of files installed on the disk.  You can then run ```
locate usr
``` to see if /usr is somewhere other than root, eg if you get /var/lib/svn/usr/rest/of/file/path you will know that /usr is there, not in root.

I think Bruno9779 may have the quickest method, however much you would like not to have to do it.

---

### Post by Wibb-untu on 2010-02-24
I managed to recover the system from the install cd in recovery mode - I simply moved all the files back to the root and now it is booting properly.

cripes. disaster fixed. time for some coffee and a change of underwear

Thanks guys for all your help, really appreciated.

---

