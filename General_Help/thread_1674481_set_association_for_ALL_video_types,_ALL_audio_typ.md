---
title: "set association for ALL video types, ALL audio types..?"
date: 2011-01-23
forum: General Help
---

### Post by Turpin on 2011-01-23
Using lxde, setting up a preconfigured environment with Remastersys to install on friends and family's machines.  So, I've linked together the applications folder under my user's account with the /usr/share/applications.  I know it's keeping filetype associations in mimeapps.list. I really don't want to have to rightclick and "open with" for every possible video and audio type, etc, not to mention that I don't have all the possible vid and audio type files on my system to do that.  Isn't there SOME way that isn't going to take hours to populate my mimeapps.list with all possible mimetypes so that I can easier edit it for all likely things the users will need?  In particular, I want VLC to open ALL audio and video files.  Is there a wildcard syntax for mimeapps.list maybe?  I've already tried video/*=vlc.desktop;    Doesn't work.  Surely there must be some intelligent way to do this.  If nothing else, I'd be happy if someone could point me to a list of all common mime filetype extensions for audio and video, because doing it all by hand and wondering if I've missed something isn't fun. I realize covering all possible filetypes is not a thing to aim for.  I just want to have all the video and audio, etc types someone is LIKELY to use somewhat preconfigured. I wouldn't make a a big deal about this on just my system because I know to "open with", "set default..", but trust me, the people I'm setting this up for can't be depended on to think of that or remember that even if I show them.

edit: added the following that I got from the vlc.desktop file.  It only took a few minutes as it turned out, but I'm a fairly advanced user.  This sort of thing could use a gui.  I expected it to be in assogiate, but no such luck. Is there actually an easier way? Or, a gui that would work in lxde that covers this?
video/dv=vlc.desktop;
video/mpeg=vlc.desktop;
video/x-mpeg=vlc.desktop;
video/msvideo=vlc.desktop;
video/quicktime=vlc.desktop;
video/x-anim=vlc.desktop;
video/x-avi=vlc.desktop;
video/x-ms-asf=vlc.desktop;
video/x-ms-wmv=vlc.desktop;
video/x-msvideo=vlc.desktop;
video/x-nsv=vlc.desktop;
video/x-flc=vlc.desktop;
video/x-fli=vlc.desktop;
application/ogg=vlc.desktop;
application/x-ogg=vlc.desktop;
application/x-matroska=vlc.desktop;
audio/x-mp3;audio/x-mpeg=vlc.desktop;
audio/mpeg;audio/x-wav=vlc.desktop;
audio/x-mpegurl=vlc.desktop;
audio/x-scpls=vlc.desktop;
audio/x-m4a=vlc.desktop;
audio/x-ms-asf=vlc.desktop;
audio/x-ms-asx=vlc.desktop;
audio/x-ms-wax=vlc.desktop;
application/vnd.rn-realmedia=vlc.desktop;
audio/x-real-audio=vlc.desktop;
audio/x-pn-realaudio=vlc.desktop;
application/x-flac=vlc.desktop;
audio/x-flac=vlc.desktop;
application/x-shockwave-flash=vlc.desktop;
misc/ultravox;audio/vnd.rn-realaudio=vlc.desktop;
audio/x-pn-aiff;audio/x-pn-au=vlc.desktop;
audio/x-pn-wav=vlc.desktop;
audio/x-pn-windows-acm=vlc.desktop;
image/vnd.rn-realpix=vlc.desktop;
video/vnd.rn-realvideo=vlc.desktop;
audio/x-pn-realaudio-plugin=vlc.desktop;
application/x-extension-mp4=vlc.desktop;
audio/mp4;video/mp4=vlc.desktop;
video/mp4v-es=vlc.desktop;
x-content/video-vcd=vlc.desktop;
x-content/video-svcd=vlc.desktop;
x-content/video-dvd=vlc.desktop;
x-content/audio-cdda=vlc.desktop;
x-content/audio-player=vlc.desktop;
video/x-flv=vlc.desktop;

---

