---
title: "Firefox 3.6 problem with Flash"
date: 2011-04-14
forum: General Help
---

### Post by Brad55 on 2011-04-14
Ok there is a web site that I help build about a year ago and it has not changed since. This is how it works you click on a picture and it opens up a small window and play a swf file, now this window has no menubar no scrollbars no toolbar. This is the code.
```
<td height="33"><a href="javascript: void(0)"onclick="window.open('movie/preview.swf','Fun At Sea','width=940,\height=705,\directories=no,\location=no,\menubar=no,\resizable=no,\scrollbars=no,\status=no,\toolbar=no');return false;" target="_blank" onMouseOver="MM_swapImage('Image9','','images/preview_r.png',1)" onMouseOut="MM_swapImgRestore()"><img src="images/preview_b.png" alt="Click to view Fun At Sea" name="Image9" width="318" height="33" border="0"></a></td>
  </tr>
```
The problem is when I try to open it up in Firefox it ask me to play it with Movie Player, and Movie Player will not play it. If I save the file and try to open it with Firefox I see a black screen but hear the sound. If I use GChrome it will not play in the pop up window, but will if I open the file. If I open the page up with Opera it all works just fine, just like it was designed to do. I can go to Youtube and play any movie clip there with not problems.

So I thought what the hell it just might be me, so I tried the same site on my Fedora 14 install and it does the same thing, the only thing I did not test on the Fedora is Opera I don't have it installed.

Can anyone tell me why this is happening.

---

### Post by Frogs Hair on 2011-04-14
I don't know what may be happening but this add-on helps a lot of users. I'm currently using the Nightly 6.0 Alpha development release , but no matter version I run , Firefox seems to run as well on the 32 bit flash with the wrapper as it does on 64 bit flash. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Brad55 on 2011-04-15
Thanks Frogs Hair that worked as far as fixing the problem in Firefox it now shows the content when I open the file. I did the test first to see if it worked.

Now the question I have will this screw up Opera because when Opera wants to play the file it wants to play it with this /usr/lib/flashplugin-installer/libflashplayer.so and as for Opera goes every thing play just the way it was intended to.

There seems to be some thing weird going on, why does Firefox and GChrome both what to save the file or to open it up with Movie Player, when Opera plays the file as intended. But if you save the file to your HD and open it up with Firefox or GChrome it plays.

---

### Post by Frogs Hair on 2011-04-15
I run Opera 11.10 and Firefox Nightly 6.0 Alpha  and have no problems , they both play video just fine  . I don't save videos and  I don't use chrome , so wouldn't much help there . I glad you have Firefox working.

---

