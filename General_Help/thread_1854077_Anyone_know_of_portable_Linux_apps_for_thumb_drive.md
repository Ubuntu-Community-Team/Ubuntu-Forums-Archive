---
title: "Anyone know of portable Linux apps for thumb drives?"
date: 2011-10-03
forum: General Help
---

### Post by pretty_whistle on 2011-10-03
I want to do as I did in Windows (R.I.P., since I no longer use Windows.....lol) where I placed portable applications on a thumb drive to run on Windows.

Does Linux have anything like this?

Mostly what I'd prefer is something like Abiword.

---

### Post by pretty_whistle on 2011-10-03
I want to do as I did in Windows (R.I.P., since I no longer use Windows.....lol) where I placed portable applications on a thumb drive to run on Windows.

Does Linux have anything like this?

Mostly what I'd prefer is something like Abiword.

---

### Post by pretty_whistle on 2011-10-03
I see this post went up twice.  PLEASE IGNORE THIS ONE AND POST REPLIES IN THE OTHER ONE.

Sorry everyone.

From oldfred
Threads merged this is correct one.

---

### Post by seawolf167 on 2011-10-03
If you want a full-fledged Ubuntu OS you can use [UNetbootin ]("http://unetbootin.sourceforge.net/")to make a bootable USB, else you could try [Portable Ubuntu ]("http://sourceforge.net/projects/portableubuntu/")(I haven't personally used it, only heard from people that have), it is supposed to run as a native Windows x32 application. Also, [here ]("http://hacktolive.org/wiki/Portable_Applications_%28Linux%29")is a [small] list of portable applications you can download.

---

### Post by seawolf167 on 2011-10-03
[Duplicate Thread]("http://ubuntuforums.org/showthread.php?p=11307799&posted=1#post11307799").

---

### Post by oldfred on 2011-10-03
Threads merged, Forum has been slow lately.

---

### Post by pretty_whistle on 2011-10-03
> **oldfred said:**
> Threads merged, Forum has been slow lately.
Oh... that's whats happened.  I thought it didn't post so I hit the back button and reposted it.

---

### Post by pretty_whistle on 2011-10-03
> **seawolf167 said:**
> If you want a full-fledged Ubuntu OS you can use [UNetbootin ]("http://unetbootin.sourceforge.net/")to make a bootable USB, else you could try [Portable Ubuntu ]("http://sourceforge.net/projects/portableubuntu/")(I haven't personally used it, only heard from people that have), it is supposed to run as a native Windows x32 application. Also, [here ]("http://hacktolive.org/wiki/Portable_Applications_%28Linux%29")is a [small] list of portable applications you can download.

I have Ubuntu installed on the HDD already, but thanx.

That list of linux portables doesn't include anything like Abiword although I found  it on sourceforge.  It was a tar.gz file but I couldn't get it to run.

---

### Post by oldfred on 2011-10-03
Are you looking for a liveCD or a full install?

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

The lighterweight versions of Ubuntu include abiword as the default as OpenOffice or LibreOffice are large applications.

---

### Post by pretty_whistle on 2011-10-03
I don't want to put OS's on the drive at all, just apps.

---

### Post by dniMretsaM on 2011-10-03
[PortableApps]("http://portableapps.com/") works under Wine. Might be worth a look.

---

### Post by pretty_whistle on 2011-10-03
> **dniMretsaM said:**
> [PortableApps]("http://portableapps.com/") works under Wine. Might be worth a look.

Wine seemed hard to understand to me.

---

### Post by dniMretsaM on 2011-10-03
> **pretty_whistle said:**
> Wine seemed hard to understand to me.

You simply have to place the program file (name.exe) in a folder, then do this in terminal:
```
wine /path/to/name.exe
```Pretty simple. There are more advanced things, but normal people only need that one command. If you have any trouble, do some searching (Google, this forum, other forums, etc.) and if you can't find a solution, just ask on here. We'll be glad to help.

---

### Post by pretty_whistle on 2011-10-03
> **dniMretsaM said:**
> You simply have to place the program file (name.exe) in a folder, then do this in terminal:
```
wine /path/to/name.exe
```Pretty simple. There are more advanced things, but normal people only need that one command. If you have any trouble, do some searching (Google, this forum, other forums, etc.) and if you can't find a solution, just ask on here. We'll be glad to help.

Thanx for that.  I'll give it a try.  :D

---

### Post by pretty_whistle on 2011-10-03
> **dniMretsaM said:**
> You simply have to place the program file (name.exe) in a folder, then do this in terminal:
```
wine /path/to/name.exe
```Pretty simple. There are more advanced things, but normal people only need that one command. If you have any trouble, do some searching (Google, this forum, other forums, etc.) and if you can't find a solution, just ask on here. We'll be glad to help.

I have a question about what to type in terminal:  Whenever I want to run a certain .exe, do I have to type that in *every time* I want to run it?

---

### Post by pretty_whistle on 2011-10-03
Another question:

Where is wine at?  The repository has wine things but says you need wine for it.  So where is it?

---

### Post by sffvba[e0rt on 2011-10-03
[http://portablelinuxapps.org/](http://portablelinuxapps.org/)


404

---

### Post by pretty_whistle on 2011-10-03
> **not found said:**
> [http://portablelinuxapps.org/](http://portablelinuxapps.org/)


404

I saw that.  It says for any to run you have to 'make executable and run".  I wouldn't know how to do that.

---

### Post by dniMretsaM on 2011-10-03
Ok, first install Wine:
```
sudo apt-get update
sudo apt-get install wine
```An EULA should come up when installing one of the packages that Wine depends on. When it appears, hit the Tab button until "<OK>" is highlighted and then press Enter.

After that, Wine will show up in your application menu with some different sub-options. All programs installed with Wine will be under the "Programs" folder within the Wine sub-options. Once you install them via [FONT=Courier New]wine /path/to/name.exe[FONT=Verdana] all programs will appear in that menu and you won't have to run that command anymore. Hope that helps![/FONT][/FONT]

---

### Post by pretty_whistle on 2011-10-03
> **dniMretsaM said:**
> Ok, first install Wine:
```
sudo apt-get update
sudo apt-get install wine
```An EULA should come up when installing one of the packages that Wine depends on. When it appears, hit the Tab button until "<OK>" is highlighted and then press Enter.

After that, Wine will show up in your application menu with some different sub-options. All programs installed under Wine will be "Programs" within the Wine sub-options. Once you install them via [FONT=Courier New]wine /path/to/name.exe[FONT=Verdana] they will appear in that menu and you won't have to run that command anymore. Hope that helps.[/FONT][/FONT]
Cool.

---

### Post by pretty_whistle on 2011-10-03
> **dniMretsaM said:**
> Ok, first install Wine:
```
sudo apt-get update
sudo apt-get install wine
```An EULA should come up when installing one of the packages that Wine depends on. When it appears, hit the Tab button until "<OK>" is highlighted and then press Enter.

After that, Wine will show up in your application menu with some different sub-options. All programs installed with Wine will be under the "Programs" folder within the Wine sub-options. Once you install them via [FONT=Courier New]wine /path/to/name.exe[FONT=Verdana] all programs will appear in that menu and you won't have to run that command anymore. Hope that helps![/FONT][/FONT]
I think I'd better quit, it's too hard.  

When I got to [FONT=Courier New]wine /path/to/name.exe, [FONT=Verdana]that lost me since I think I'm supposed to put in a file path and I just say, "What path?  It's a flash drive whose icon appeared on the desktop."<-- that's not a path and I know it.[/FONT]

[FONT=Verdana]Plus the name of the .exe is super long so I wonder, "Will it even work that way?"  The file name is :[/FONT]
[/FONT]   	 	 	 	 	 	  [FONT=Courier New]LibreOfficePortable_3.4.3_MultilingualNormal.paf.exe[/FONT]

---

### Post by dniMretsaM on 2011-10-03
To find the path, open up Nautilus and got to root. Now go to the media folder (or it might be Media with a capital M}, it should list the thumbdrive (it might have a weird name). Once you find it, copy the name and the run this in terminal:
```
wine /media/nameofthumbdrive/rest/of/path/to/LibreOfficePortable_3.4.3_MultilingualNormal.paf.exe
```

"nameofthumbdrive" is the name of your thunbdrive as displayed in /media/ and "rest/of/path/to/" is the path to the .exe file within the thumbdrive.

EDIT: You should be installing PortableApps (download this from the site I linked you to earlier) with Wine, not the actual app that is portable. Sorry for the confusion. So download the PortableApps program file (the .exe) and put it in your Home folder. Rename it to "portableapps.exe" and then run this in terminal:
```
wine ~/portableapps.exe
```

---

### Post by pretty_whistle on 2011-10-03
> **dniMretsaM said:**
> To find the path, open up Nautilus and got to root. Now go to the media folder (or it might be Media with a capital M}, it should list the thumbdrive (it might have a weird name). Once you find it, copy the name and the run this in terminal:
```
wine /media/nameofthumbdrive/rest/of/path/to/LibreOfficePortable_3.4.3_MultilingualNormal.paf.exe
```"rest/of/path/to/" is the path to the .exe file within the thumbdrive.
I decided to right click the exe to see if open with wine was there-it was and just installed it.  That was easy.  Didn't think of looking there before..... :rolleyes:

---

### Post by pretty_whistle on 2011-10-03
I tried opening writer but it says :

Archive:  /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe
[/media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe or
          /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe.zip, and cannot find /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe.ZIP, period.

------------------------------
I'll quit will I'm behind.  Too many issues to overcome with wine, as I thought.

Thanx though.

---

### Post by dniMretsaM on 2011-10-03
> **pretty_whistle said:**
> I tried opening writer but it says :

Archive:  /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe
[/media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe or
          /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe.zip, and cannot find /media/6162-3532/LibreOffice/LibreOfficePortable/LibreOfficeWriterPortable.exe.ZIP, period.

------------------------------
I'll quit will I'm behind.  Too many issues to overcome with wine, as I thought.

Thanx though.

Installing with right-click has never worked for me. Read the edit to my previous post. Don't give up, you can do this. Think of how good you'll feel when you get it working (which you will).

---

### Post by pretty_whistle on 2011-10-03
> **dniMretsaM said:**
> Installing with right-click has never worked for me. Read the edit to my previous post. Don't give up, you can do this. Think of how good you'll feel when you get it working (which you will).

I went back to that post and did all that.  The portableapps menu came up only at first when it was installed.  Thereafter when I try to start it again I get that archive error message I posted above.  Hitting anything with .exe gets that same error actually.

Edit:  I see the portableapps folder has an autorun.inf file in it.  Does that mean portableapps should automatically run when I plug in the flash drive?  Well, I tried placing a copy of the portableapps folder contents in the root of the drive-that failed, but the portableapps folder deleted all the content by itself-no more portableapps, it's gone now.  Weird.

Edit #2 :  I got it to run, the menu I mean.  However Oo would not open, abiword kept crashing.

Just updating this post.

Due to continued wine issues, this endeavor has been discontinued.  Just an fyi.

---

### Post by sffvba[e0rt on 2011-10-03
> **pretty_whistle said:**
> I saw that.  It says for any to run you have to 'make executable and run".  I wouldn't know how to do that.

... and once you know how you will be able to do it ;)

[Here]("http://ma65p.wordpress.com/2008/08/04/how-to-make-a-file-executable-in-ubuntu/") is what a quick Google came up with... and I am sure if it isn't clear enough there are many here that would gladly assist you with getting it right :)


404

---

### Post by pretty_whistle on 2011-10-03
> **not found said:**
> ... and once you know how you will be able to do it ;)

[Here]("http://ma65p.wordpress.com/2008/08/04/how-to-make-a-file-executable-in-ubuntu/") is what a quick Google came up with... and I am sure if it isn't clear enough there are many here that would gladly assist you with getting it right :)


404

Thanx.

Edit:  Tried it.  Error message says:  No such file/directory.

Not found, in other words <taking advantage to make a pun out of your name..lol>

---

### Post by sffvba[e0rt on 2011-10-03
> **pretty_whistle said:**
> Thanx.

Edit:  Tried it.  Error message says:  No such file/directory.

...That isn't giving much info...

From what I can gather from [http://portablelinuxapps.org](http://portablelinuxapps.org) you simply download the app you want... say to your desktop.  

In Nautilus -> 
right-click the downloaded file -> 
go to properties ->
Permissions -> 
and click on "Allow Executing..."

Then you should be able to double-click and use it...


404

---

### Post by pretty_whistle on 2011-10-03
> **not found said:**
> ...That isn't giving much info...

From what I can gather from [http://portablelinuxapps.org](http://portablelinuxapps.org) you simply download the app you want... say to your desktop.  

In Nautilus -> 
right-click the downloaded file -> 
go to properties ->
Permissions -> 
and click on "Allow Executing..."

Then you should be able to double-click and use it...


404

Failed.  It unclicks itself after I just clicked it.

---

### Post by sffvba[e0rt on 2011-10-03
> **pretty_whistle said:**
> Failed.  It unclicks itself after I just clicked it.

Strange.  I just tried it and it worked a charm...


404

---

### Post by pretty_whistle on 2011-10-04
Update:

I said at the start of this thread that I wanted mostly to put something like Abiword on it.  Solved this by a workaround/hack.  Here's what I did:



I opened LibreOffice Writer on the desktop and saved it to the flash drive-yes, *a blank one*.  I named it LibreOffice Writer (for ease of use since it'll function as a document template, so to speak).

Whenever I need to type a document on the drive I type it in this saved blank one.  When done with it, I choose 'save as' and give it whatever is the name of the document I just typed.

Keep the blank writer on the flash drive *permanently*.  What this does is it enables the blank one to be used sort of like a template-a LibreOffice template, that being a blank Writer.

Whenever I need to type another document, I just write it into the blank saved writer on the drive, then when done choose 'save as' (has to always be 'save as' or it'll save the document into the blank one and not save is as a separate one and that you don't want).



Cool.  I did the same trick on my BlackBerry with Documents to Go because I didn't have the premium version.

Cool.  This thread is solved now.  Glad I remembered how I did that! :D :D
):P

---

