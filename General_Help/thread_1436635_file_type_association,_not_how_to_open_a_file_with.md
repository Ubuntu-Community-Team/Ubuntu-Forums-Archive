---
title: "file type association, not how to open a file with a different app"
date: 2010-03-22
forum: General Help
---

### Post by thaitang on 2010-03-22
i have probably a bit of a n00b question here but I cannot find a solution. I started using opera the other day and i like it a lot, except it saves webpages as MHT files. when I tried to open one of the MHT's using firefox the file type for all MHT files (I have a lot) changed to being text files and open with mousepad now. 

I know I can easily just right click on the file and choose opera to open the files, but then when I try to open a regular text file opera opens that instead of mousepad. I work with text files all day as well as opening webpages offline, so i need to try and fix this. I am sure there is a simple solution but everything I read is someone explainign how to change how to open file types with different apps and not how to actually change the file type.

any help or suggestions would be appreciated.
thanx
tt

oh yeah, is there a way to convert and if so batch convert MHT files to HTML so that yes, they save as a page with an associated file folder. much better for me.

---

### Post by ScarletWyvern on 2010-03-22
You're trying to set it up so that text files will open with an application other than Opera, for example, right?

Right click the file -> Properties -> Open With -> Pick the program. All files of that type will open with the app you chose.

---

### Post by gadolinio on 2010-03-23
Errrm why is it that MHT files and text files would shre the same application to be opened with?
I don't quite catch that.

Anyway, maybe editing this file can help you:
./.local/share/applications/mimeapps.list
If you right click the mht file and go to properties, you'll see the filetype, something like application/x-mht perhaps.
Well in the mimeapps.list file you'll have something like:
application/x-mht=gedit.desktop
if they're opened with the text editor. Try changind that to opera.
And make sure that text files are still opened with gedit, and other webpages with the browser you want:
text/css=gedit.desktop;openoffice.org-writer.desktop;
text/html=epiphany.desktop;
text/plain=gedit.desktop;

---

### Post by thaitang on 2010-03-23
too bad I was hoping to attach a screenshot to make it clear, but perhaps I do not have enough posts under my belt to do so, the attachment icon does nothing.

So, anyways I truly do understand that I can right click on any file and under properties change the default application to open that type of file. However, this is not my issue, somehow all MHT files have been assinged a filetype as being a TEXT file. Any browser can still open them fine, but now being assigned as file type TEXT either all my gedit by default tries to open MHT files so I have to right click on MHT files to choose (other app) opera or firefox to open them, or set a browser to open txt files and then have to manually right click to choose to open real text files with gedit.

I am sure that is about a s clear as mud. But if I right click on any file and choose to view properties there is a description of what TYPE of file the file is. Something that does not have a drop down enu to change. it is the description that shows up in any file manager listing the file types, I just happen to be using Thunar so I am not quite sure how it looks using Nautilus but I am sure it is similar.

Anywas it is that file type I need to change from being a text file being an HTML/MHT/broswer type file, so only browsers open them by default.

oh well I hope that makes more sense?

cheers,
tt

---

### Post by thaitang on 2010-03-23
ok looks like I saw the add attachments window after I submitted the last reply. so I think it would clear things up 100% if I actually added a screenshot, so I hope this works.

cheers,
tt

---

### Post by thaitang on 2010-03-23
This is driving me a tad bit crazy so I just wanted to give it a bump. I am sure the fix is probably fairly simple or straightforward.

thanx,
tt

---

### Post by gadolinio on 2010-03-23
/home/username/.local/share/applications contains a file called mimeapps.list and another file called mimeinfo.cache. They contain filetypes and the applications that open them.
In my case, if i right-click a mht file the properties window states it's a "mime encapsulated web archive (application/x-mimearchive)".
In mimeinfo.cache i have this line: application/x-mimearchive=opera.desktop
and in mimeapps.list, this one: application/x-mimearchive=firefox.desktop;epiphany.desktop;
I'd try inserting those (with the browser you want), then reboot, and see if a mht file is recognized as application/x-mimearchive. (Make a backup copy of the files before editing them, just in case...)

---

### Post by eksasol on 2010-03-23
The app Ubuntu Tweak has a section called File Type Manager, but you have to edit them one by one so not too useful. Now if it could select mutiple files then it would be quite useful.

---

### Post by thaitang on 2010-05-07
I finally gave up and gave up on using Opera because continually switching the appropriate applications between text and mht files to view them was getting to be a major PITA!

But now, the same problem has just cropped up in tha past day or two with MS Word/.doc files and text files.

When I double click on a .doc file gedit tries to open it even though it is listed in properties as a .doc file. I change the application to open .doc files to Open Office and when I click on a .txt (I always name my regular plain text files with a .txt ext) to open it, Open Office is started and tries to open the file. Grrrr.

I do not do much in the way of maintenance other than updates usually every week or two b/c I am on dial up. I can think for the life of me what I might have changed in the past week, never mind day or two that would have caused this problem. It is the exact same problem I was having with saved .mht files from opera and .txt files.

I used .doc files regularly, so that is why I know this has only recently happened within a day or two since I neer previously had this problem opening .doc files with the correct application, in my case Open Office, ever!

Any ideas here? I can not simply decide not to use .doc files like I easily decided to drop using Opera for FireFox once again.

Many might suggest updating to the next flavour of Ubuntu, which I will do soon enough when I can d/load on high speed, but it will still bug me what this problem is. I cannot believe for the life of me that there is not a .conf file somewhere that lists all file types and their application association, only I gave up looking for it last time I had this problem. But there has to be a config file where this info is ket and referred to by the kernel when an action is made to open a file whatever the type. I am getting in way over my head here, but that sounds sort of logical anyways.

Any help or advice and I would sure appreciate it.

PS just like last time, I understand full well how to change the preferred application for opening any given file type. That is not my issue. Of course I am having to do that each time I open either a .doc or a .txt file depending on which application I have last set as the default. I hope that makes sense.

cheers,
tt

---

### Post by gadolinio on 2010-05-07
This might be helpful:
[http://stackoverflow.com/questions/30931/register-file-extensions-mime-types-in-linux](http://stackoverflow.com/questions/30931/register-file-extensions-mime-types-in-linux)

---

### Post by thaitang on 2010-05-11
> This might be helpful:
[http://stackoverflow.com/questions/3...types-in-linux]("http://stackoverflow.com/questions/30931/register-file-extensions-mime-types-in-linux")
Interesting, but it does not explore what might bei going on here that file types are not being associated correctly.

Is there really no one here who knows their way around the Linux kernel or Ubuntu better than me, I mean I know pretty much squat, which might have some relevent ideas or suggestions?

I am sure it us going to end up being user (yes this user) error, but for the life of me I cannot think of doing anything that might have brought this on.

When it first started happening between .MHT ad .TXT files, after installing Opera, I simply ended up writing the problem off as being Opera induced. But now, I have been opening and using .DOC regulalry for years using OpenOffice without any such glitches.

I look forward to hearing them if you do :)

cheers,
tt

---

### Post by EuriskoXP on 2010-08-11
I have a similar problem. I have convinced my grandfather to switch to Linux from Vista, and the setup is smooth, except for some reason the MHT files are being seen as and opened as txt (with gedit).

I want to be clear, i know how to change the preferred app for a file type! the problem is that it is seeing the mht as a txt, so the preferred app for mht isnt being called at all. is there a fix for this? 

FYI we are both using 10.04, and my install sees the difference between mht and txt, his sees both as txt...

---

### Post by renkinjutsu on 2010-08-11
What's going on here is that the OS is seeing the MHT files as being regular text files. Use the file command to see what the system sees the file as (probably the same as a regular text file)

```
file blah.mht
```

So the solution or workaround would probably be for the developers add a new filetype to recognize, or you can make do with a small script

```
\#!/bin/bash
opts="${1}"

if [ "$(${opts}|grep -i \.mht )" = "" ]; then
mousepad ${opts}
else
opera ${1}
fi
exit
```
This will check the file name to see if it contains the .mht in the name

save that as mhtopener, then chmod it to make it executable```
chmod +x mhtopener
```
Then put it somewhere in your PATH, probably /usr/bin or put it into ${HOME}/bin if possible. Now you can set your file browser to use that script to open up your files. Go to alternate commands and just put in mhtopener.

This method is not foolproof though, say, you can have a text file name this.mht.isjustatextfile would open in opera. Someone more skilled will be able to write an improved script

---

### Post by EuriskoXP on 2010-08-11
It reads as "news or mail text" (text file like you predicted)

Its worth noting that this is NOT simply an 'oversight' in the distro, because my other install is the same version (10.04) and recognizes the same file appropriately as "multipart/related; start=<op.mh"

Both systems are 10.04, same updates installed! Why are they seeing the file differently?

---

### Post by EuriskoXP on 2010-08-12
Found a fix, much neater than the launcher script. Grab a nifty lil program called assogiate, and create the custom MIME type.

[http://ubuntugenius.wordpress.com/2009/11/19/create-a-new-mimetype-for-mht-web-archives-in-ubuntu/](http://ubuntugenius.wordpress.com/2009/11/19/create-a-new-mimetype-for-mht-web-archives-in-ubuntu/)

HOWEVER, this still doesn't explain why .mht read perfectly fine with no tweaking on the laptop, but needed this fix on the desktop, since both are running the same version 10.04

---

### Post by demauk on 2010-10-28
> **gadolinio said:**
> ... maybe editing this file can help you:
./.local/share/applications/mimeapps.list


Thanks, gadolinio!

I was using xubuntu, so most of my text files had Mousepad first and OOo Writer second. Then I switched to regular ubuntu and removed xubuntu. All my text files were opening in Writer, even after I said I wanted it to remember gedit for the next time.

I suspect having the Mousepad entry when the editor was no longer available tripped the system up a bit.

I just opened mimeapps.list and removed all mousepad references.

---

### Post by gadolinio on 2010-10-28
> **demauk said:**
> Thanks, gadolinio!

I was using xubuntu, so most of my text files had Mousepad first and OOo Writer second. Then I switched to regular ubuntu and removed xubuntu. All my text files were opening in Writer, even after I said I wanted it to remember gedit for the next time.

I suspect having the Mousepad entry when the editor was no longer available tripped the system up a bit.

I just opened mimeapps.list and removed all mousepad references.


glad you found it useful!

---

