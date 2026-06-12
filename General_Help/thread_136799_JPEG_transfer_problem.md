---
title: "JPEG transfer problem"
date: 2006-02-26
forum: General Help
---

### Post by fidel_26 on 2006-02-26
I just installed ubuntu 5.10.  Today I tried to transfer some phots that I have on CD, and only about half worked.  When i opened File Browser to look at the pics that failed, the previews wouldn't load, and I received a weird error saying that even though the files have .JPEG extensions, they are actually text files, and that I should only open them if I created them, and that I should edit them to show the correct extension.  

The problem is, I can't get them open with anything, and I can't change the file type to anything else, because they actually are JPEG files.

Sorry for the length, and the confusion, but if anyone has any ideas, please let me know....you can IM me if that will help sort out what the problem is.

Basically, all I'm after is getting my pics transfered back onto my PC...

Thanks

---

### Post by pestilence4hr on 2006-02-26
Are you sure the CD's are good?  This doesn't sound like a ubuntu-specific issue.  Have you tried copying the cd on other machines?  Another thing, there isn't 100% compatibility between old cdroms and cd-r's, so if the cdrom is fairly old (~10 years) that might be an issue.

---

### Post by pestilence4hr on 2006-02-26
Oh, another related question, if you copy the cd a few different times is it always the same pictures that have problems?

---

### Post by fidel_26 on 2006-02-26
I've tried the CD a few different times, and I've had the same problems everytime, which, you're right, points to a problem with the files.  I'm going to try the CD on my office PC (Win XP Pro) tomorrow, and see what happens there.  Hopefully I'll be able to salvage the files there.

Age shouldn't be an issue, as the CD is only a couple of weeks old.  The mystery to me is why it's telling me that it's a text file...they are all from the same batch of pics.

I'll see what happens tomorrow on WinXP and let you know...thanks

---

### Post by fidel_26 on 2006-02-27
In case anyone was wondering, it looks like some sort of problem with the media....

---

### Post by Kevinator on 2006-02-27
I've seen the message you are talking about, but only once. It seems to be saying that the apparent type of the file (implied by the file "extension") is different from the  type of data that the file seems to contain. This is a sort of red flag, indicating that the file might be a trojan of some sort. In most cases, it probably just means that the content sniffing failed (e.g., your JPEG images probably are JPEGs, with some ASCII metadata, but they got misidentified as ASCII text).

I think the message was asking you to change the file extension to .txt (to match the apparent type of the data in the file), but that would obviously be the wrong thing to do, since the type really is JPEG. Try opening the files in an editor or viewer (rather than opening them through the file browser) and I bet it will work. I don't know how to make Nautilus recognize that the files are OK. This is new to me as well.

---

### Post by milehigh on 2006-05-28
I'm having the same problem, except that I'm transfering jpegs directly from the camera with usb. The jpegs display perfectly in nautilus and gqview. If I add them to a web page and display it in Firefox (from the hard drive), it's OK. However, when I upload it using gftp, it doesn't display the image over the internet; you just see the html page missing the photo. The icon displayed in gftp is different than the normal (round) one for jpeg. It's not the camera or the card; I tranfered it to a Windows XP laptop that shares the same internet connection and uploaded it with Core ftp, and it displays just fine. :-?

---

### Post by milehigh on 2006-05-28
Forgot to mention, I'm running Dapper (installed beta and have been applying all updates). And this is from a screenshot of gftp:
[IMG]http://www.jims-pages.com/snapshot1.png[/IMG]

---

