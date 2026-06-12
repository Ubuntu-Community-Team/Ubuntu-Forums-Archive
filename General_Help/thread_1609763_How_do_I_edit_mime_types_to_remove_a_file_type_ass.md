---
title: "How do I edit mime types to remove a file type association"
date: 2010-10-30
forum: General Help
---

### Post by Handssolow on 2010-10-30
I installed a trial copy of Anquet Map V06 under Wine then decided to remove it. Afterwards I could find many remnants associated with the Anquet program which I've deleted. Except what remains is an association between my .gpx files with Anquet and that includes and any new gpx file I download. My interpretation is that during the install process an association has been created with the gpx file type and the Anquet map program. This is what I want to stop.

If I download a .gpx file and look at it's properties I see-
Type: GPX File -Anquet Mapsv06 (application/x-wine-extension-gpx)

I found this file and it's contents-
/.local/share/mime/application/x-wine-extension-gpx.xml

<mime-type type="application/x-wine-extension-gpx">
&#8722;
<!--
Created automatically by update-mime-database. DO NOT EDIT!
-->
<glob pattern="*.gpx"/>
<comment>GPX File - Anquet Maps v06</comment>
</mime-type>

Running "sudo update-mime-database /usr/share/mime" and rebooting didn't remove the association.

How can I stop the Anquet name making as association with my gpx files?

---

### Post by hwttdz on 2010-10-30
Right click on a gpx file and hit properties, then go to the open with tab, change it to the application you want, and hit ok/save...

---

### Post by Handssolow on 2010-10-31
Thanks for your reply. When I open the "Open With" tab I see-

Select an application to open xxxx.gpx and other files of the type "GPXFile-Anquet Maps V06"

A Wine application is named as the  program and this I've removed however, this doesn't change the Basic Properties of the file type. All my gpx files are still named as being associated with Anquet. There's no change if I update mime. Incidentally I'm not sure what programs I should select to open gpx files, if any.

Don't I need to change a mime configuration file then update the mime database?

---

### Post by Handssolow on 2010-11-16
bump

Selecting to download a gpx file from a website today, the default Open option is open with a Wine application. I don't want this default option, namely my gpx files associated with a Wine application. Neither do I want Properties to show my gpx files being identified as "GPX File-Anquet Maps V06 (application/x-wine-extension-gpx).

How do I change things globally, to remove the associations between gpx files with Wine and Anquet Maps?

---

### Post by patocardo on 2010-11-18
Handssolow. Did you find the solution? I have the same problem but with chm files.

---

### Post by Handssolow on 2010-11-18
No I didn't. I spent another hour recently looking for some more information. It's not a big issue just an irritation that file properties shows my gpx files associated with Wine. At least Open with, no longer defaults to Wine. If I selected reset it would revert to Wine.

---

### Post by patocardo on 2010-11-27
Handdolow:
   I think I found the solution:

1. Right-click on a file with the mimetype in trouble
2. Click on "Properties" menu element
3. Click on "Open with" flap
4. Select the application name you don't want to use any more
5. Click "Remove" button
6. Close the window

Than worked for me

---

### Post by muneson on 2011-04-07
Had similar problems six months later, so maybe this won't reach you. However, I found what I needed here:

[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-modifying.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-modifying.html.en)

Marcus

---

### Post by Handssolow on 2011-04-07
Thanks Marcus, I'll study the information in your link for next time,
Eventually it was sorted when I moved to a new hard drive and a fresh install.

---

### Post by WorMzy on 2011-04-07
Did you try editing the mimeapps.list file under "~/.local/share/applications/"?

---

### Post by zeehio on 2011-04-12
I cooked a solution of my own:

I recently installed and uninstalled a Wine application. Everything was fine except that the ".dat" extension had been associated with the application.

The first thing I tried was, from Nautilus, "Right click, Properties" "Open With" Remove. I could fix the default application, but the "file type" and the icon was still not right.

Then I found out ~/.local/share/mime/application/

I removed the file corresponding to x-wine-extension-dat.xml
I executed update-mime-database ~/.local/share/mime/

I expected the problem to be solved.

I am not sure, but I believe that wine can recreate the removed file, because in the Wine Windows registry the Mime association still exists.

Therefore, I executed $ wine ~/.wine/drive_c/windows/regedit.exe

I looked for ".dat" and similar associations at HKEY_CLASSES_ROOT
I deleted those keys.

Problem solved.

(I posted a copy of this solution [here]("http://www.sergioller.com/drupal/node/12").)

---

