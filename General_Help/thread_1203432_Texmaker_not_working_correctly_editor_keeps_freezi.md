---
title: "Texmaker not working correctly: editor keeps freezing"
date: 2009-07-03
forum: General Help
---

### Post by dpm_edinburgh on 2009-07-03
Does anybody else have a problem with the Texmaker version from the repository?  Every so often, the editor will freeze and prevent me from editing my file.  I can still highlight text, but cannot add or delete any content.

Closing the file and reopening it will not fix the problem; I have to exit Texmaker.

Is there a fix for this?  It never used to do this.

(I'm on Gnome.)

---

### Post by dpm_edinburgh on 2009-07-10
Nobody?

---

### Post by entropy1 on 2009-07-10
I know of no solution for Texmaker.  I used Kile instead for a while, but then Xcan suggested (see [http://ubuntuforums.org/showthread.php?t=1150983](http://ubuntuforums.org/showthread.php?t=1150983)) the LaTeX plugin for gedit.  Now I use gedit most of the time.

---

### Post by entropy1 on 2009-07-11
A solution that worked for me is to use a more recent version of Texmaker than is available in the repos.:

1) Uninstall repository-version of Texmaker using synaptic.
2) Download latest appropriate .deb version of Texmaker from

[http://www.xm1math.net/texmaker/download.html#linux](http://www.xm1math.net/texmaker/download.html#linux)

3) After you download the appropriate .deb file, right click and select   Open with "GDebi Package Installer".

4) Enjoy the latest version of Texmaker.

---

### Post by dpm_edinburgh on 2009-07-11
Thanks, that seems to have fixed it.

---

### Post by skywatcher on 2009-07-14
I hope you don't mind me jumping onto this thread, but maybe someone can give me some advice.

I installed TeXlive from CD, set the PATH and tested it from the terminal according to the documentation. Everything worked OK. Then I installed the latest version of Texmaker (1.9.2) and it too seemed to work up to a point, except when I tried to run LaTeX using either Quick Build or LaTeX from the Tools menu. Then I discovered the following:

The link to Texmaker is under Applications > Office. When I open Texmaker by clicking on this link, I experience the problem mentioned above. HOWEVER: when I run Texmaker from the terminal by typing 'texmaker', everything works. This is weird, since the command in System > Preferences > Main Menu > Office > Texmaker is also 'texmaker'. What's the difference?

---

