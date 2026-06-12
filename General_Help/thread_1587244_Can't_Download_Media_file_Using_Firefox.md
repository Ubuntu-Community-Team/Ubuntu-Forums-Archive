---
title: "Can't Download Media file Using Firefox?"
date: 2010-10-03
forum: General Help
---

### Post by aisajib on 2010-10-03
Hello Everyone! I've been running a weird problem since last two days on my Ubuntu 10.04 LTS. I'm using the latest version of Mozilla Firefox on my computer. For last two days, I'm unable to download anything using my Firefox. Whenever I click on a, say mp3 download link, the browser starts to play it instead of downloading the link. Some download websites don't provide direct link to download so I can't just right click and choose Save link as. 

I need a solution. I don't want Firefox to play the files inside the browser. I want the download dialogue box to appear instead. This weird behavior has started just two days ago. Before that, everything was fine.

See the screenshot below:

[IMG]http://img695.imageshack.us/img695/6582/mp3wd.png[/IMG]

*If you give it a close look you'll notice that an mp3 file (sky colored tab indicated the active tab) is being played in the browser.*

It may be mentioned that I'm using a snow leopard theme on my ubuntu but that's not what causing the weird behavior of Firefox. I activated this theme about a week ago and everything was fine even after I activated it. So, it's not the theme that is making the problem.

Anyone please help me with this problem. I can't download any media file to my computer because of this.

---

### Post by aisajib on 2010-10-03
Image resizing doesn't work? :o I resized its width to 600 pixels. It's still showing its full width. :(

---

### Post by lovinglinux on 2010-10-03
Please use the attachment feature to add images to your posts. Is really annoying to scroll horizontally to read messages, because of big images.

Close Firefox, go to your Firefox profile folder, located under ~/.mozilla/firefox/<profilename> and move the file **mimeTypes.rdf** to another location, rename it or delete it. This will reset your Applications preferences and should fix your problem.

---

### Post by aisajib on 2010-10-03
Sorry for the inconvenience. I attached the image in traditional way which asks for image URL instead of uploading. So, I uploaded the image on imageshack.us and provided the link here. I didn't know image resizing doesn't work.

Thanks for your response, but I'm afraid of losing other settings in the way you mentioned above. I'm using a different theme that made some changes with my browser's font settings. I love the new fonts as I'm a big fan of typography. As you said it resets application preference, I may lose the font settings as well. I am looking for specific way to troubleshoot the problem with media file downloading.

---

### Post by lovinglinux on 2010-10-03
> **aisajib said:**
> Sorry for the inconvenience. I attached the image in traditional way which asks for image URL instead of uploading. So, I uploaded the image on imageshack.us and provided the link here. I didn't know image resizing doesn't work.

Thanks for your response, but I'm afraid of losing other settings in the way you mentioned above. I'm using a different theme that made some changes with my browser's font settings. I love the new fonts as I'm a big fan of typography. As you said it resets application preference, I may lose the font settings as well. I am looking for specific way to troubleshoot the problem with media file downloading.

Deleting **mimeTypes.rdf** doesn't reset all your Firefox settings, only the ones related to which applications opens what and if each file should be saved or opened with an application. You can backup** mimeTypes.rdf** and put it back any time you want. If you are so worried, then backup your entire profile.

Anyway, I gave you instructions for your specific problem. You shouldn't see any changes in fonts or other Firefox settings.

---

### Post by aisajib on 2010-10-08
Oh, thanks! I thought I'd lose all other settings. I'll try it soon. Thanks again for your help. :)

---

### Post by shahan on 2010-10-08
> **aisajib said:**
> Oh, thanks! I thought I'd lose all other settings. I'll try it soon. Thanks again for your help. :)
you can use some Addons for better downloading experience. You can try, Downloadthemall
Click Tools>Addons
then select Get Addons
then type on the "search" box "Download Them All"
then install....

---

### Post by madhi19 on 2010-10-08
> **shahan said:**
> you can use some Addons for better downloading experience. You can try, Downloadthemall
Click Tools>Addons
then select Get Addons
then type on the "search" box "Download Them All"
then install....
Not a bad suggestion but I would have to recommend DownloadHelper instead. Way more user friendly.

---

### Post by aisajib on 2010-10-08
I'm a very old user of Download Them All and I still have this plugin installed on my computer. But it won't work if Firefox doesn't detect a download url. For example, dta starts working when the regular download prompt box shows up and I ask dta to take over. I can also use the url on dta manager to begin downloading but you know not all download sites provide direct download link.

---

### Post by aisajib on 2010-10-08
> Not a bad suggestion but I would have to recommend DownloadHelper instead. Way more user friendly.

I have both plugins installed. DownloadHelper works for media downloading when it is shown in the current page. DtA is a download manager, actually. Say an alternative to Internet Download Manager.

However, DownloadHelper does not work on my computer when download url starts on Movie Player instead of downloading.

---

### Post by shahan on 2010-10-08
yo can try File>Save Page As
(though its not an absolute solution.)

---

### Post by aisajib on 2010-10-08
That doesn't work. It starts downloading the php file. If in the case of above screenshot, when the media file is being played, I can't right click. right clicking opens up the options from Movie Player.

---

### Post by lovinglinux on 2010-10-08
I just made some tests and Firefox opens mp3 files embedded with the plugin by default. I'm trying to figure out a way of changing that, but I wasn't successful so far.

---

### Post by aisajib on 2010-10-09
> **lovinglinux said:**
> Please use the attachment feature to add images to your posts. Is really annoying to scroll horizontally to read messages, because of big images.

Close Firefox, go to your Firefox profile folder, located under ~/.mozilla/firefox/<profilename> and move the file **mimeTypes.rdf** to another location, rename it or delete it. This will reset your Applications preferences and should fix your problem.


I can't find that .mozilla folder anywhere in root/home folder. :(

---

### Post by lovinglinux on 2010-10-09
> **aisajib said:**
> I can't find that .mozilla folder anywhere in root/home folder. :(

Don't bother. Deleting the suggested file won't work anyway. I tried. About the profile location, you need to press CTRL+H to see hidden folders. It is t under /home/username/.mozilla/firefox/<profilename>

---

