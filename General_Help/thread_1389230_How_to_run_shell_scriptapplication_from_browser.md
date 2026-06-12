---
title: "How to run shell script/application from browser"
date: 2010-01-24
forum: General Help
---

### Post by madu on 2010-01-24
Hello,

I am looking for a method to run a shell script or open an application through the web browser.
For example, open OpenOffice from the browser (without going through the menus).
Is it possible?
My ultimate goal to pass an argument through the browser to a script. I know it is pretty far fetched for my very limited abilities but I wanna try. For example I want to pass an URL or a text string from the browser to a shell script.

Any leads are greatly appreciated.

Cheers.

---

### Post by lovinglinux on 2010-01-24
You could create a fake protocol to launch OpenOffice.

_Registering the protocol_

Firefox gets its protocol information from its hidden settings.

1. In the Location bar, type about:config, and press Enter.

2. Right-click anywhere in the grid, choose New, then String. 

3. In the "Enter the preference name" prompt, type in "network.protocol-handler.app.oow" and press OK.

4. In the "Enter string value" prompt, type "/usr/bin/oowriter"

Now create a bookmark using "oow:///" as URL. When you click the bookmark, OpenOffice Writer will be opened. If Firefox prompts you to choose an application, simply browse the folder "/usr/bin" and select "oowriter", even if there is already an option for "oowriter" on the application list. Then tick "Remember my choice for oow links" and hit "OK". OpenOffice Writer will start on another window.

To launch a script, you can apply the same technique, but parsing arguments is a different story.

It is pretty easy to create an extension to launch a bash script. Please specify which arguments you want to parse, the name of the script and a name to give to the extension. Paste the code of the script inside code tags here and I will create it for you later today.

---

### Post by madu on 2010-01-24
> **lovinglinux said:**
> You could create a fake protocol to launch OpenOffice.

_Registering the protocol_

Firefox gets its protocol information from its hidden settings.

1. In the Location bar, type about:config, and press Enter.

2. Right-click anywhere in the grid, choose New, then String. 

3. In the "Enter the preference name" prompt, type in "network.protocol-handler.app.oow" and press OK.

4. In the "Enter string value" prompt, type "/usr/bin/oowriter"

Now create a bookmark using "oow:///" as URL. When you click the bookmark, OpenOffice Writer will be opened. If Firefox prompts you to choose an application, simply browse the folder "/usr/bin" and select "oowriter", even if there is already an option for "oowriter" on the application list. Then tick "Remember my choice for oow links" and hit "OK". OpenOffice Writer will start on another window.

To launch a script, you can apply the same technique, but parsing arguments is a different story.

It is pretty easy to create an extension to launch a bash script. Please specify which arguments you want to parse, the name of the script and a name to give to the extension. Paste the code of the script inside code tags here and I will create it for you later today.

Thanks alot for that LovingLinux.

I followed the steps you mentioned but when I type "oow:///"  I get an "alert" saying "Firefox doesn't know how to open this address, becasue protocol (oow) isn't associated with any program".

What am I doing wrong?

Cheers buddy.

---

### Post by lovinglinux on 2010-01-24
> **madu said:**
> Thanks alot for that LovingLinux.

I followed the steps you mentioned but when I type "oow:///"  I get an "alert" saying "Firefox doesn't know how to open this address, becasue protocol (oow) isn't associated with any program".

What am I doing wrong?

Cheers buddy.

I need to test it, because it has been a while since I used that hack. I will try to fix this after lunch. Do you want the extension to launch the script?

---

### Post by madu on 2010-01-24
> **lovinglinux said:**
> I need to test it, because it has been a while since I used that hack. I will try to fix this after lunch. Do you want the extension to launch the script?

Thanks Buddy.
Yes I do want the extension although I haven't really planned through. I have several things in mind but my main objective is to learn it. If you could put my script in to an extension that would be awesome. I can learn extensions too.

A skeleton version of one of the things I'd want to do is to download a video from YT and convert it.

So for example:

> URL = [http://youtube.com/xxxx](http://youtube.com/xxxx)
youtube-dl URL
ffmpeg -i *.flv -ar 22050 URL.mp4
rm *.flv


Something like that. So I want to be able to parse the URL.

Sorry I do not have a solid script. Would this be OK?

Thanks heaps again.

---

### Post by lovinglinux on 2010-01-24
> **madu said:**
> Thanks Buddy.
Yes I do want the extension although I haven't really planned through. I have several things in mind but my main objective is to learn it. If you could put my script in to an extension that would be awesome. I can learn extensions too.

A skeleton version of one of the things I'd want to do is to download a video from YT and convert it.

So for example:




Something like that. So I want to be able to parse the URL.

Sorry I do not have a solid script. Would this be OK?

Thanks heaps again.

Yep that would be easy. I will work on it tonight, I will probably send to you tomorrow. I will build a basic extension with your script and you can learn and improve it from there. What name do you want to give it? Also I need an e-mail address to be used as the ID of the extension. It doesn't have to be a valid e-mail, but is better to be one that you actually own. You could create for example a gmail account for it like, [email]myyoutubedownloader@gmail.com[/email] (send me by pm).

---

### Post by madu on 2010-01-24
> **lovinglinux said:**
> Yep that would be easy. I will work on it tonight, I will probably send to you tomorrow. I will build a basic extension with your script and you can learn and improve it from there. What name do you want to give it? Also I need an e-mail address to be used as the ID of the extension. It doesn't have to be a valid e-mail, but is better to be one that you actually own. You could create for example a gmail account for it like, [email]myyoutubedownloader@gmail.com[/email] (send me by pm).

I really appreciate the help buddy.
I'm in the process of learning things which I usually take for granted everyday (like extensions).
For the name, MyYouTubeDownloader sounds good :D

Will PM you the email.

Cheers.

---

### Post by lovinglinux on 2010-01-24
The extension is attached. Download it, then rename the file extension from .zip to  .xpi then open from Firefox to install. After installing and restarting Firefox, right-click on a toolbar and select "Customize", then drag the "MyYouTubeDownloader" button to the toolbar.

To use it, click the "MyYouTubeDownloader" button and insert the YouTube video ID, not the URL. For example for the URL below (pretty funny video btw):

[http://www.youtube.com/watch?v=**yX8yrOAjfKM**](http://www.youtube.com/watch?v=yX8yrOAjfKM)

The ID is **yX8yrOAjfKM**.

The extension will download the video to your home directory, then convert it to mp4, then move the converted file to your Desktop and delete the original source.

An alert about the finished download will be displayed if you have zenity installed.

Please keep in mind this is a very simple prototype. It won't show any error messages if something goes wrong. But it should be enough to get you started.

To learn more about extension development, create an account at [Mozilla Add-ons](https://addons.mozilla.org/en-US/firefox/users/register), login and visit the [Developer Hub](https://addons.mozilla.org/en-US/developers). It has lot's of info and resources.

Have fun.

---

### Post by madu on 2010-01-24
> **lovinglinux said:**
> The extension is attached. Download it, then rename the file extension from .zip to  .xpi then open from Firefox to install. After installing and restarting Firefox, right-click on a toolbar and select "Customize", then drag the "MyYouTubeDownloader" button to the toolbar.

To use it, click the "MyYouTubeDownloader" button and insert the YouTube video ID, not the URL. For example for the URL below (pretty funny video btw):

[http://www.youtube.com/watch?v=**yX8yrOAjfKM**](http://www.youtube.com/watch?v=yX8yrOAjfKM)

The ID is **yX8yrOAjfKM**.

The extension will download the video to your home directory, then convert it to mp4, then move the converted file to your Desktop and delete the original source.

An alert about the finished download will be displayed if you have zenity installed.

Please keep in mind this is a very simple prototype. It won't show any error messages if something goes wrong. But it should be enough to get you started.

To learn more about extension development, create an account at [Mozilla Add-ons](https://addons.mozilla.org/en-US/firefox/users/register), login and visit the [Developer Hub](https://addons.mozilla.org/en-US/developers). It has lot's of info and resources.

Have fun.


Thank you so much for that LovingLinux.
I did not have much time but I installed it and everything worked great!

Thank you very much buddy. I need to go through the files carefully but I think all the magic happens in Chrome/content/getvideo.sh file right? 

I will check that tutorial out. This is really interesting :popcorn:

Thanks a million again for taking your time out for doing this.

Cheers.

---

### Post by lovinglinux on 2010-01-24
> **madu said:**
> Thank you so much for that LovingLinux.
I did not have much time but I installed it and everything worked great!

Thank you very much buddy. I need to go through the files carefully but I think all the magic happens in Chrome/content/getvideo.sh file right? 

I will check that tutorial out. This is really interesting :popcorn:

Thanks a million again for taking your time out for doing this.

Cheers.

You are welcome. The extension basically works like this:

1) overlay.xul is the file that overlays the button on the toolbar
2) when you click the button it calls a javascript function on overlay.js 
3) that function launches getvideo.xul, where you can enter the ID. It also monitors the output of getvideo.xul. Once you fill the ID an click OK, the function on overlay.js continues. It then checks if ffmpeg and youtube-dl are installed then parse the ID entered to overlay.sh,  which performs the download using youtube-dl and the conversion using ffmpeg.

---

### Post by madu on 2010-01-25
> **lovinglinux said:**
> You are welcome. The extension basically works like this:

1) overlay.xul is the file that overlays the button on the toolbar
2) when you click the button it calls a javascript function on overlay.js 
3) that function launches getvideo.xul, where you can enter the ID. It also monitors the output of getvideo.xul. Once you fill the ID an click OK, the function on overlay.js continues. It then checks if ffmpeg and youtube-dl are installed then parse the ID entered to overlay.sh,  which performs the download using youtube-dl and the conversion using ffmpeg.

Thank you for that LovingLinux.
overlay.js seems to be most difficult part here :| didnt see that before..
I'll go through the material and see... thanks again mate...

---

### Post by lovinglinux on 2010-01-25
> **madu said:**
> Thank you for that LovingLinux.
overlay.js seems to be most difficult part here :| didnt see that before..
I'll go through the material and see... thanks again mate...

Yup. Be prepared for lots of reading :)

I knew nothing about javascript when I started to make Firefox extensions and it still eludes me. But with [all the material provided by Mozilla](https://developer.mozilla.org/En) I was able to create what I believe is a very nice extension, called [FoxMediaCenter](https://addons.mozilla.org/en-US/firefox/addon/10991). It works perfectly for my needs. I have been working on it for over a year. When I started it was completely different and very basic. Most functions were bash script parsers like the one I made for you. Now the extension is entirely developed with javascript and sqlite databases.

---

### Post by madu on 2010-01-25
> **lovinglinux said:**
> Yup. Be prepared for lots of reading :)

I knew nothing about javascript when I started to make Firefox extensions and it still eludes me. But with [all the material provided by Mozilla](https://developer.mozilla.org/En) I was able to create what I believe is a very nice extension, called [FoxMediaCenter](https://addons.mozilla.org/en-US/firefox/addon/10991). It works perfectly for my needs. I have been working on it for over a year. When I started it was completely different and very basic. Most functions were bash script parsers like the one I made for you. Now the extension is entirely developed with javascript and sqlite databases.

Thank you LovingLinux. Thats encouraging.
Just wanna ask you, what is the relation between extensions and Jetpack?
I can make extensions using Jetpack too right? Which method should one follow?

Thank you.

---

### Post by lovinglinux on 2010-01-25
> **madu said:**
> Thank you LovingLinux. Thats encouraging.
Just wanna ask you, what is the relation between extensions and Jetpack?
I can make extensions using Jetpack too right? Which method should one follow?

Thank you.

Jetpack is a new framework for doing things like extensions and scripts (like greasemonkey). I have tried it a few months back, but I don't know how developed it is right now or how easy it is to use it, in comparison with the regular extension API. As far as I know, is not a replacement. There is a post on Mozilla development blog that says extensions are not going anywhere.

I would recommend trying to make a simple extension with both and see which one is easier for you and which offers the features you need.

---

### Post by madu on 2010-01-25
> **lovinglinux said:**
> Jetpack is a new framework for doing things like extensions and scripts (like greasemonkey). I have tried it a few months back, but I don't know how developed it is right now or how easy it is to use it, in comparison with the regular extension API. As far as I know, is not a replacement. There is a post on Mozilla development blog that says extensions are not going anywhere.

I would recommend trying to make a simple extension with both and see which one is easier for you and which offers the features you need.

Thank you very much buddy.
Started reading the introductory tutorials and also came across Jetpack. It is pretty overwhelming to say the least, but really exciting... :D

Thank you very much LovingLinux. 
Trying out your extension :P But I think I cant make best use of it since I am not in US :(

Thanks again.

---

### Post by lovinglinux on 2010-01-25
> **madu said:**
> Trying out your extension :P But I think I cant make best use of it since I am not in US :(

Why? I live in Brazil and it works for me :)

---

### Post by madu on 2010-01-25
> **lovinglinux said:**
> Why? I live in Brazil and it works for me :)

Got it now.
I was thinking it as something else.. 
Nice work.. Dont even want to imagine the coding if that.. :-\"

---

### Post by lovinglinux on 2010-01-25
> **madu said:**
> Got it now.
I was thinking it as something else.. 
Nice work.. Dont even want to imagine the coding if that.. :-\"
Thanks. It has a lot of code. In fact, 32,151 lines. Probably because I'm not a good programmer :)

---

