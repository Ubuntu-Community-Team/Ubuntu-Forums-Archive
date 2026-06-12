---
title: "download manager with browser integration?"
date: 2010-09-16
forum: General Help
---

### Post by fuzzylogic25 on 2010-09-16
Does a download manager that can integrate with the browsers cookies exist? For example, I am a member of rapidshare.com and if I am logged into that website, firefox stores this information and i get direct access to download links. 

so if we had a link [www.rapidshare.com/files/4336345/ubuntu.zip](www.rapidshare.com/files/4336345/ubuntu.zip) it would normally take u to a html file first where u have to click a button to wait for 1 min before download starts, but since i am registered, all i do is log in and then if i try to download that link it gives me the direct zip file. in windows i used many download managers that could integrate with firefox to see that i am logged in and give me the direct file.

actually i believe it just relied on cookies from firefox. so even other sites like megaupload.com would work once i logged in.

is there any program that does this?

---

### Post by sikander3786 on 2010-09-16
There is an add-on for Firefox, [Downthemall]("https://addons.mozilla.org/en-US/firefox/addon/201/"). Might help in the current situation.

---

### Post by fuzzylogic25 on 2010-09-20
i was hoping for a program besides a plugin as i want to handle 1000+ links.

---

### Post by k33bz on 2010-09-20
I know there is one, I used to use it all the time, cant remember the name right off. I know it was a kde application, but it could work inside gnome.

---

### Post by Tosa on 2010-09-20
I use jDownloader, [http://jdownloader.com/](http://jdownloader.com/)

It handles all major file sharing services both as free and with payed accounts. I find it very useful for downloading multiple files.

---

### Post by fuzzylogic25 on 2010-09-20
> **k33bz said:**
> I know there is one, I used to use it all the time, cant remember the name right off. I know it was a kde application, but it could work inside gnome.

was it Kget?

---

### Post by k33bz on 2010-09-20
> **fuzzylogic25 said:**
> was it Kget?

yup, thats the one I was referring to. :)

---

### Post by fuzzylogic25 on 2010-09-21
ok so just to be clear i want to explain what i mean by browser integration.

if i download a link [www.rapidshare.com/files/2352/ubuntu.zip](www.rapidshare.com/files/2352/ubuntu.zip) using a download manager, it would just result in a HTML file. that HTML file will say something like "please click here for free download or here for premium download". So it is not a direct link.

However, if I login to rapidshare using firefox then it remains logged in, even if i check 2 weeks later im still logged into rapidshare. Then when i add the link above to the download manager it will download the file, it will be a direct link. So firefox keeps some cookie im guessing, to show its logged in and the download manager needs to see this.

is this what you mean for Kget?

also i know some programs like Jdownloader can maintain account information for popular sites like rapidshare. But I also have access to some unpopular ones like hotfile and mediafire. So in these situations, having a program that can read firefox cookies...or download whatever firefox would download (a direct link instead of a indirect one) is what i need.

---

### Post by gandaran on 2010-09-21
> **fuzzylogic25 said:**
> ok so just to be clear i want to explain what i mean by browser integration.

if i download a link [www.rapidshare.com/files/2352/ubuntu.zip](www.rapidshare.com/files/2352/ubuntu.zip) using a download manager, it would just result in a HTML file. that HTML file will say something like "please click here for free download or here for premium download". So it is not a direct link.

However, if I login to rapidshare using firefox then it remains logged in, even if i check 2 weeks later im still logged into rapidshare. Then when i add the link above to the download manager it will download the file, it will be a direct link. So firefox keeps some cookie im guessing, to show its logged in and the download manager needs to see this.

is this what you mean for Kget?

also i know some programs like Jdownloader can maintain account information for popular sites like rapidshare. But I also have access to some unpopular ones like hotfile and mediafire. So in these situations, having a program that can read firefox cookies...or download whatever firefox would download (a direct link instead of a indirect one) is what i need.
kget is for Kde, for gnome use Gwget, I dont know if gwget is what you want, try it, have gwget running in the system tray and right click a download link in firefox and copy the link no need to paste in gwget, the download link will be there in gwget waiting for you to start download.

---

### Post by fuzzylogic25 on 2010-09-21
I tried Gwget and it didnt do it either. So a link like [www.rapidshare.com/files/345/ubuntu.zip](www.rapidshare.com/files/345/ubuntu.zip) was returned as a html file.

Where as when using firefox to download that link, it returns the zip file (provided I have logged into rapidshare first of course).

So I am still trying to find a program that can download/see the link the way firefox can.

This will also be a problem when you are trying to download from other sites which require you to login. Once logged in, you can download files but download managers need to be able to detect that you are logged in.

---

### Post by Henery on 2010-10-16
I see on rapidshare under rapidtools tab there is a manager it works with winblows. It also shows a other os download with the pic of the linux pengin but I am not sure how to use it downloaded tried running in terminal no go and tried with wine as there is a exe in the zip.

Maybe someone else can try and get it working in ubuntu!

---

### Post by inhiway on 2010-10-16
You might take a look at FatRat and see if it suits your purposes.  It's in the repositories.

---

### Post by fuzzylogic25 on 2010-10-17
sigh. the frustrations of moving away from windows. Tried fatrat too. It will not capture downloads from firefox where registrations are required.

So like I said before, if there is some link (say [www.downloads.com/ubuntu.zip](www.downloads.com/ubuntu.zip)) but the link will ONLY return the actual zip file if your logged in, fatrat wont notice it, even if firefox does (once logged in of course).

We need download managers that can fully integrate with firefox and see the cookies or something.

---

### Post by fuzzylogic25 on 2010-10-17
The firefox plugin DOWNLOADTHEMALL is the only good thing out there. BUT, this is still useless when it comes to downloading large amounts of links (say 100s to 1000s) and also if you have heaps of firefox browsers open. I find firefox to get really slow once you install plugins and have heaps of windows/tabs.

I have no resorted to using my laptop with Windows XP for downloads.

---

### Post by sikander3786 on 2010-10-17
> The firefox plugin DOWNLOADTHEMALL is the only good thing out there.

You can also use GWGet and integrate it into firefox using the extension flashgot.

[https://help.ubuntu.com/community/DownloadManager](https://help.ubuntu.com/community/DownloadManager)

[https://addons.mozilla.org/en-US/firefox/addon/220/](https://addons.mozilla.org/en-US/firefox/addon/220/)

---

### Post by fuzzylogic25 on 2010-10-17
yep tried that too. pretty much every program that flashgot can interact with has the same problem, it cant recognize links where you require log in access even though firefox can.

FlashGot only works with the firefox plugin downloadthemall.

---

### Post by yh88 on 2010-10-18
Wow, didn't that "linux download manager" take very long time in discussion,
why there still isn't a good download manager?
We are in 2010 for god sake.

---

### Post by ankspo71 on 2010-10-18
Hi,
I don't think this will have any browser integration, but Tucan is supposed to be good at handling these types of multi-part downloads from file hosting sites by grabbing the files files within the links. It is in the universe repositories of Ubuntu 10.10 so you can find it in Synaptic or Software Center.

Here is a writeup about it:
[http://www.econowics.com/linux/318/install-tucan-rapidshare-megaupload-etc-download-manager-in-ubuntu-linux/](http://www.econowics.com/linux/318/install-tucan-rapidshare-megaupload-etc-download-manager-in-ubuntu-linux/)

Here is the homepage:
[http://tucaneando.com/features.html](http://tucaneando.com/features.html)

I don't use a download manager, but I thought it might help to mention Tucan.

---

### Post by fuzzylogic25 on 2010-10-18
tucan helps by having all these sharing sites added. but it doesnt allow for registered accounts in all of them. registered accounts is what I have. So its still not a good tool.

Really if they just had a download manager that could fully integrate with firefox, you would not need to worry about anything else!

---

### Post by ankspo71 on 2010-10-18
Hi Again,
Well, no, I now see that Tucan does lack that feature for most of those sites, but technically it does have premium user logins for rapidshare and megaupload at least. I just installed Tucan to check because in that link above I posted it talked about premium access to rapidshare. I wanted to make sure I wasn't recommending something that wasn't useful at all.

---

