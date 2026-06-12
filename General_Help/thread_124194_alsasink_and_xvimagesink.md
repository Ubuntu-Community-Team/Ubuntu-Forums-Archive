---
title: "alsasink and xvimagesink"
date: 2006-01-31
forum: General Help
---

### Post by Specialsauce on 2006-01-31
every time i go to certain web pages, i get this error that konquerer cannot init driver alsasink and it cant init driver xvimagesink.... and then it all crashes. 

its REALLY pissing me off, and im about to switch to SUSE if i cant find a straight answer. 

i did find something that said that it fixed it if you change the engine from gstreamer to xine, but i have no clue how to do it. and yes, i have searched

---

### Post by Michel F on 2006-02-02
If you have not tried it before, I would think that the way to switch from gstreamer to xine is:
- make sure both kaffeine-gstreamer (by default) and kaffeine-xine packages are installed;
- launch kaffeine, configuration menu, engine, select xine.

Now, having said that, I have a similar problem as yours. If I right-click on a .mov file in Konqueror, I have the possibilty to "prevview with gstreamer part". If I do that, then I have the two messages complaining about alsasink and xvimagesink, and then Konqueror crashes.

I am using Kubuntu 5.10 freshly installed and the ATI proprietary driver.

Any indication on this strange behaviour ?

---

### Post by Neo Ex on 2006-02-02
Also if you use the Xine engine in Kaffeine, Konqueror may give you errors concerned to alsasink and xvimagesink, like if it has tried to use GStremear instead of Xine. But that's what he's tried to do. You have to change the file associations in KControl -> File associations -> [File type] -> Embedding.
The first item is GStreamerPart, but you have to set it to Kaffeine, or, if you have it, to KMPlayer (it's better: with KMPlayer Konqueror won't crash after viewing a movie or listening to a music file).

---

### Post by Michel F on 2006-02-03
You are right. I also installed the kdemultimedia package which contains two simple readers, kaboodle and Noatun. Both do the job if you select them in the FileAssociation/Embedding dialog box (at least for the type of video film I tested, ie small clips taken on an olympus digital camera).
However, these are only turnarounds. There seems to be a bug with gstreamer/konqueror. Hope this is solved in future version or that someone knows how to solve it.

---

### Post by Neo Ex on 2006-02-03
I think it's not a problem that has GStreamer with Konqueror: I think it's a GStreamer problem, because I receive the same errors also if I try to use Kaffeine (as a stand-alone program) with the GStreamer engine.

---

### Post by Michel F on 2006-02-06
I can not confirm your last post. For me everything is well with kaffeine-gstreamer standalone. The only occurence where I have the "alsasink" and "xvideosink" error messages is when I right-click "preview with GstreamertPart". I did the test on several file formats (quicktime, avi, wmf, mpeg).
So I still think this is a Konqueror "bug" with GtreamerPart. Of course, what I call a "bug" may only be the result of an improper use or configuration on my side. 

I also gave a try at the Dapper Flight CD 3 Live. Same issue out of the box !!! But the Gstreamer version is still 0.8. Seems like 0.10 not implemented yet.

I understand that few users are experiencing that, because probably most of you use Firefox as a webbrowser with the apporpriate netscape plugin. So embedding might not be an issue there. However, I would very much like to understand why the "preview" feature in Konqueror is failing with GstreamerPart.

Any thoughts, ideas or experience out there ?

---

