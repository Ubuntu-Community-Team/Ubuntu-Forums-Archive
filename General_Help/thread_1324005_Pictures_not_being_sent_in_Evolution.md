---
title: "Pictures not being sent in Evolution"
date: 2009-11-12
forum: General Help
---

### Post by sayantandas on 2009-11-12
Hi ,
I have a problem with Evolution in ubuntu 9.10. Everything works fine except the fact that I cannot send pictures with emails.
the emails somehow goes off without the pictures.i have been testing them by sending it to myself as well . It does not work. even pictures in my signatures are not being sent. 
i have enabled all possible options for HTML emails. still doesnt work.
Other mail clients like spicebird works very nicely.

any help will be appreciated. 

thanks.

---

### Post by sayantandas on 2009-11-21
bump

---

### Post by akakingess on 2009-11-21
Just to clarify, you are attaching pictures to the emails, and they are not showing up on the other end? Or are you pasting pictures into the body of the email? Let me know and I will try to do some troubleshooting/investigating on it.

---

### Post by thoth3g on 2009-11-29
It's not my intention to hijack a thread but wanted to add something to this. 
I know that you guys mention the "gmail" option when setting up mail. That's only good for pop not imap. Imap is pretty much the only way to go for me as I've had the email address for about 5 years. 
I've setup my gmail (imap) from both evolution and thunderbird (my pref). I've been over the settings multiple times and I'm not a stranger to protocols and where to plug things in. Everything works fine in both until I try to send a message that has a pasted image or if I attach a picture. It consistently fails in each then. If it's strictly a text message then sending works fine.
Any thoughts? (I know that the server settings are correct, anything outside of the actual settings comes to mind?)

---

### Post by sayantandas on 2009-12-01
> **akakingess said:**
> Just to clarify, you are attaching pictures to the emails, and they are not showing up on the other end? Or are you pasting pictures into the body of the email? Let me know and I will try to do some troubleshooting/investigating on it.

Hi, 

attachments go well. its the pictures when inserted into the body of the email, including the signature pictures does not get sent.

---

### Post by ankspo71 on 2009-12-01
Hi,
When I was trying to send emails with pictures in Ubuntu 9.04, I found out that when I created an email with pictures in the body of the message, I also had to include the same pictures in the attachments so that they would be displayed in the body. I haven't tried sending pictures with Evolution in Ubuntu 9.10 yet.

Currently I am having an even more mysterious problem sending mails to and from gmail and verizon (both webmail). It appears that random images won't go through to the other person and I can see the url in the picture box looking for a picture on the other user's desktop. (c:/documents/etc...). Very strange.

I mentioned both problems because I'm not sure which one you might be having. The first problem has a work around though. Hope it helps.
James

---

### Post by plucky on 2009-12-01
> **sayantandas said:**
> Hi, 

attachments go well. its the pictures when inserted into the body of the email, including the signature pictures does not get sent.

Go to **Edit > Preferences > Composer Preferences > General** and tick the box that says **Format messages in HTML** will allow the pictures to be sent in the body of the message.

I think the default is "Plain Text" messages is the reason that pictures don't get sent.

Good Luck

---

### Post by thoth3g on 2009-12-01
Yes, it appears that you're situation is a bit different indeed. Regular text messages send fine on mine but sending fails if there is ANY ATTACHMENT. This is my second installation of Ubuntu 9.10 (had other kinks to work out) with the same attachment situation.:rolleyes:

---

### Post by ClimberBear on 2010-06-01
> **plucky said:**
> Go to **Edit > Preferences > Composer Preferences > General** and tick the box that says **Format messages in HTML** will allow the pictures to be sent in the body of the message.

I think the default is "Plain Text" messages is the reason that pictures don't get sent.

Good Luck

Hi,

I'm having the same problem, and every time is worse.

In Jauny and Karmic, it only happens with images in signatures.

Now, it doesn't send embeded images in any case.

If you check the e-mail, from "Sent mails folders" or other, you see (activating see all - Ctrl-U), the following html code:

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 TRANSITIONAL//EN">
<HTML>
<HEAD>
  <META HTTP-EQUIV="Content-Type" CONTENT="text/html; CHARSET=UTF-8">
  <META NAME="GENERATOR" CONTENT="GtkHTML/3.28.3">
</HEAD>
<BODY>
<IMG SRC="" ALIGN="bottom" BORDER="0"><BR>
<IMG SRC="" ALIGN="bottom" BORDER="0"><BR>
<BR>
<BR>
<BR>

As you can see, the image name is empty (double quoted). This process is done by evolution in the moment it send the e-mail.

---

### Post by sgosnell on 2010-06-01
See if [this post ](http://ubuntuforums.org/showpost.php?p=6854524&postcount=4) helps.  It specifically addresses a problem with attaching Picasa images, but you may be able to use it in a more general configuration.

I just tried sending an embedded photo in a mail message from Evolution, and was successful.  One thing to check may be in the composer preferences, check the box for Encode filenames in an Outlook/Gmail way.

---

### Post by Subito Piano on 2010-06-29
Same problem here with 9.04 - i posted elsewhere but so far nobody has answers.  I might try the picasa suggestion but i don't know how to modify the code--????

---

### Post by practic on 2011-06-09
There was a problem in the "evolution-rss" package which was causing this behaviour. It was supposed to be fixed last year, but I'm still seeing the problem with Ubuntu 11.04 and the latest Evolution. 

The solution for now is to remove the "evolution-rss" package with Synaptic.

---

### Post by djahma on 2012-01-20
> **practic said:**
> There was a problem in the "evolution-rss" package which was causing this behaviour. It was supposed to be fixed last year, but I'm still seeing the problem with Ubuntu 11.04 and the latest Evolution. 

The solution for now is to remove the "evolution-rss" package with Synaptic.

Thanks! this solution works. This had troubled me for weeks! I even switched to thunderbird because of it.

---

