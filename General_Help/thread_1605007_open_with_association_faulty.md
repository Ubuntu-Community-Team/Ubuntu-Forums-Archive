---
title: "open with association faulty"
date: 2010-10-24
forum: General Help
---

### Post by marbour on 2010-10-24
Hi.

After installing Handbrake, MKVs are "open with" associated with it.

I have repeatedly changed the "open with" association to make these files open with VLC to no avail.

I have tried both 2bl-clicking VLC and "custom command" while clicking the "remember" option.

I am running an updated Lucid installation.

Can anyone tell me what is wrong?

Best regards.

---

### Post by papibe on 2010-10-24
Forget me if you already try this, but you never know:

[INDENT]Right click on the mkv file,
Select properties.
Go to the tab named "Open with"
Select VLC
Close properties[/INDENT]

Now it should be open VLC when you double click the file.

Good Luck!

---

### Post by marbour on 2010-10-25
Hi.

Thanks for trying: This is **exactly** what I said I'd done higher up.

Still left with this problem.

Any other ideas?

Regards

Marc

---

### Post by marbour on 2010-10-30
I am coming back to this issue with development:

No open with associations I change with the right-click, open with and memorize stick.

None at all... Clips, MP3s, wine exe's.

I need help for this is very irritating.

Best regards

Marc

---

### Post by papibe on 2010-10-30
It looks like the changes are not written to the mime database (located in ~/.local/share/mime/). This could happen because either you don't have permission, the database change format, or it got corrupted.

**Permissions**

Maybe for accident (using sudo), the owner or permissions got change. Do this to get them back:
```
$ cd /home
$ sudo chown -R youruser:youruser  youruser
$ chmod -R u+rw
```
Try changing the file association again.

**Format**

Run this:
```
sudo update-mime-database.real -V ~/.local/share/mime/
```
Restart your machine and try again.

**Other trick**

Some people use an app called "Ubuntu Tweak". I haven't use it, but at this point it wouldn't hurt. Follow this tutorial: [How To Manage File Associations In Ubuntu With Ubuntu Tweak]("http://www.liberiangeek.net/2010/05/how-to-manage-file-association-in-ubuntu-with-ubuntu-tweak/").

**Corrupted**

This is the last resort. It will reset All your gnome settings to the default. If you have spend time customizing your desktop you may want to avoid it:

Press Alt-Ctrl-F1
Login to your account in text mode. Then
```
$ sudo service gdm stop
$ rm -rf .gnome .gnome2 .gconf .gconfd .metacity
$ sudo service gdm restart
```
If you have kubuntu, change gdm for kdm. Try changing the file association again.

Good Luck!

---

### Post by mc4man on 2010-10-30
Edit: (removed most of comment
This made me take a closer look at files when opened from the open with/other application menu
The remember option is setting the app chosen as the default, (which I believe it shouldn't do), and may also lead to what was noticed here in later posts.




If you wish to see where set look in ~/.local/share/applications/mimeapps.list

When an association for mkv is made this line is created and or adjusted, first listed is the default.
Ex.
video/x-matroska=vlc.desktop;userapp-mplay-E15PIV.desktop;totem-xine.desktop;

---

### Post by marbour on 2010-10-31
@papibe

Thanks. I tried everything you suggested up to ubuntu tweak.

All perms were ok, but I did what you suggested anyways. To no avail might I add.

Ubuntu Tweak did the trick...

BUT... Strangely enough, when I went to edit some file associations, they were associated with Handbrake but clicking edit showed VLC just as I had asked. Saving as is left the Handbrake association in place. 

I had to edit->select handbrake->select vlc->save sor the association to work.

And I found out that out of my 3 Ubuntu systems, 2 of them were "affected" and both had Handbrake installed. It seems that Handbrake is "polluting" the mime associations agressively.

I can't part from Handbrake... But I now have a fix.

Thanks a lot for helping.

---

### Post by JohnAStebbins on 2010-11-01
> **marbour said:**
> @papibe

Thanks. I tried everything you suggested up to ubuntu tweak.

All perms were ok, but I did what you suggested anyways. To no avail might I add.

Ubuntu Tweak did the trick...

BUT... Strangely enough, when I went to edit some file associations, they were associated with Handbrake but clicking edit showed VLC just as I had asked. Saving as is left the Handbrake association in place. 

I had to edit->select handbrake->select vlc->save sor the association to work.

And I found out that out of my 3 Ubuntu systems, 2 of them were "affected" and both had Handbrake installed. It seems that Handbrake is "polluting" the mime associations agressively.

I can't part from Handbrake... But I now have a fix.

Thanks a lot for helping.
HandBrake installs the following ghb.desktop file that establishes it's mime associations:
```

[Desktop Entry]
Name=HandBrake
GenericName=DVD Ripper
Comment=Transcodes DVD and other media
Exec=ghb
Icon=hb-icon
Terminal=false
Encoding=UTF-8
Type=Application
Categories=GTK;AudioVideo;Video;
MimeType=application/ogg;application/x-extension-mp4;application/x-flac;application/x-matroska;application/x-ogg;audio/ac3;audio/mp4;audio/mpeg;audio/ogg;audio/x-flac;audio/x-matroska;audio/x-mp3;audio/x-mpeg;audio/x-vorbis;video/mp4;video/mp4v-es;video/mpeg;video/msvideo;video/quicktime;video/vnd.divx;video/x-avi;video/x-m4v;video/x-matroska;video/x-mpeg;video/x-ogm+ogg;video/x-theora+ogg;x-content/video-dvd;x-content/video-vcd;x-content/video-svcd;

```
This should **not** override your default 'Open with' options.  It should merely add additional 'Open with' options to these file types.  This is how it behaves on all my systems.  And I've not had any reports of your issue happening to others.  I'm not sure how your system got out of wack.  

If anyone can give a clue what went wrong and whether there is anything I could do to prevent it from happening to others, speak up.

---

### Post by marbour on 2010-11-01
@[JohnAStebbins]("http://ubuntuforums.org/member.php?u=657190")

Thanks for the details.

Is there a way I can contribute to your inquiry? 

I've checked what you wrote and you are right indeed. Would you like me to try to reproduce the problem in a virtualmachine and render it available to you if I can?

Best regards.

MArc

---

### Post by JohnAStebbins on 2010-11-01
> **marbour said:**
> @[JohnAStebbins]("http://ubuntuforums.org/member.php?u=657190")

Thanks for the details.

Is there a way I can contribute to your inquiry? 

I've checked what you wrote and you are right indeed. Would you like me to try to reproduce the problem in a virtualmachine and render it available to you if I can?

Best regards.

MArc
Thanks for the offer.  Right now, I can't think how I would approach debugging the problem.  I don't know enough about how gnome/installer/nautilus uses the desktop file.  So an install where the problem doesn't occur is a null result because I already know it works in most circumstances and an install where the problem does occur leaves me with no idea where to start looking.  This is going to require a bit of googling and my bet is I'll have to read some nautilus source code since this kind of thing is rarely documented adequately in linux.

---

### Post by mc4man on 2010-11-01
Just to ck. I'd set up a new user, login, and see if handbrake has changed the default for it's registered mime types 'system wide'

(ubuntu tweak would only be setting locally, ie, adding or editing a line ~/.local/share/applications/mimeapps.list

A new user would have  the default as it was after handbrake was installed, for most commom a/v types the default would be totem unless changed locally.

The mis-behavior of the 'remember this application...' option on folders is clear, it also seems to be improper for files, though to what extent not sure (other than changing the default which I don't think it should.

---

