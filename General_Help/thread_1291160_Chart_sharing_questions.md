---
title: "Chart sharing questions"
date: 2009-10-14
forum: General Help
---

### Post by jwaclawsky on 2009-10-14
How could I best go about sharing some charts with a number of people on a conference all? Most of the other people would have windows machines. Is there a facility like NetMeeting or compatable with NetMeeting (a windows program) available for Ubuntu? ...or could someone recommend a website that allows Linux as well a windows machines to share charts (under my control). Thanks for any suggestions and assistance.

---

### Post by Lars Noodén on 2009-10-14
I forgot what netmeeting was a copy of originally.  No matter.

Here is one possibility that I have recently heard of people testing:
  [https://www.webhuddle.com/](https://www.webhuddle.com/)

There used to be an add-on for krfb to allow one to many, but IMHO it makes since to add it to the program itself:
[https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/223083](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/223083)

---

### Post by Lars Noodén on 2009-10-14
A more experimental option, and maybe low ROI, would be to use ffmpeg to record your X11 session and use vlc or icecast to stream it live.  Then you can used some VoIP tool for the audio.  However, I myself am having trouble with that, so it's an experimental option.  ;)

---

### Post by Lars Noodén on 2009-10-14
pidgin also has something in the works, 
[http://developer.pidgin.im/wiki/VirtualClassroom](http://developer.pidgin.im/wiki/VirtualClassroom)

So does coccinella
[http://coccinella.im/](http://coccinella.im/)

And even inkscape
[http://www.inkscape.org/](http://www.inkscape.org/)


To be a bit flippant, maybe wubi could be useful for your clients still on legacy platforms.  ;)  Or a LiveCD with the conferencing tools.

---

### Post by jwaclawsky on 2009-10-15
I tried a couple of the links suggested by Lars, who responded to my original request and webhuddle looks the closest to what I need: something  simple that lets me display charts (I think??). Has anyone used "WebHuddle" yet? I signed up and tried to upload a sample presentation and no matter what I do or try to upload, I get the same error message: 

Error uploading your file. Confirm it is a .ppt or .sxi file (or a .zip file containing GIF/JPEG images)

Has anyone got this to work? Thanks for any assistance.

---

### Post by BbUiDgZ on 2009-10-15
> **jwaclawsky said:**
> I tried a couple of the links suggested by Lars, who responded to my original request and webhuddle looks the closest to what I need: something  simple that lets me display charts (I think??). Has anyone used "WebHuddle" yet? I signed up and tried to upload a sample presentation and no matter what I do or try to upload, I get the same error message: 

Error uploading your file. Confirm it is a .ppt or .sxi file (or a .zip file containing GIF/JPEG images)

Has anyone got this to work? Thanks for any assistance.
never used webhuddle myself but after reading this thread i too think it looks the best of the bunch.

a ".ppt" file is a microsoft format, and i'd take a guess that its not supported by webhuddle. A ".sxi" file is from openoffice and looks by that message to be fully supported.

zip the ppt file before you upload it.


have a look at [Google Wave](http://wave.google.com) its still in beta but one to keep your eye on ;)

---

### Post by jwaclawsky on 2009-10-16
Ok, I'll try WebHuddle with the .sxi OpenOffice format. The message seems to indicate that ".ppt" are supported too. I'll check out Google Wave too. Thanks

---

### Post by BbUiDgZ on 2009-10-20
> **jwaclawsky said:**
> Ok, I'll try WebHuddle with the .sxi OpenOffice format. The message seems to indicate that ".ppt" are supported too. I'll check out Google Wave too. Thanks

according to the WH docs you can install ppt support at server side.

ofcourse you will need to run your own server which is somthing i'm looking to do in the near future. i'll update then

---

### Post by Lars Noodén on 2009-10-21
> **BbUiDgZ said:**
> according to the WH docs you can install ppt support at server side.

ofcourse you will need to run your own server which is somthing i'm looking to do in the near future. i'll update then

Can you say how well it does with OpenDocument format?

---

### Post by BbUiDgZ on 2009-10-23
> **Lars Noodén said:**
> Can you say how well it does with OpenDocument format?

ok i've installed and successfully ran webhuddle on a server 2003 machine here at our company. to get full ppt support you need to install and configure openoffice on the server (please see the docs on sourceforge). webhuddle will do exactly what it says on the tin. you can view and mark slide in real time, it has a wee chat window and you can record you webmeeting to file. one great feature (although i found i a bit laggy) is the desktop sharing which means you could run powerpoint on your own machine and share your desktop ;)

i'm pretty certian a java developer (which i am not) could get alot more from this application.

TIP: webhuddle breaks ppt slides into a series of images. save your slides as jpegs and upload in that format if the webhuddle server you are using dosnt support ppt, this way you can use the drawing tool in real time to highlight and draw directly onto your slides.

---

