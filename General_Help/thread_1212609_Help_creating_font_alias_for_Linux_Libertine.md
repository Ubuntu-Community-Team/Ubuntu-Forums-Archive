---
title: "Help creating font alias for Linux Libertine?"
date: 2009-07-13
forum: General Help
---

### Post by gldearman on 2009-07-13
Hi, all,

Those of you who use the font Linux Libertine have noticed that it breaks when you update to Jaunty.  Jaunty's version of the Linux Libertine package includes the OTF version of the font, which has an incompatible name ("Linux Libertine O" instead of "Linux Libertine").

So, all of my Open Office documents written in Linux Libertine (which is a lot, since that was my default font for Open Office Writer) now point to a font name that does not exist.  So, they are rendered in a default font, and look horrible.

There is a bug report for this [here]("https://bugs.launchpad.net/ubuntu/+source/linux-libertine/+bug/318551").  The bug report suggests that it can be fixed by assigning a font alias; i.e., telling applications that the font name "Linux Libertine" refers to the font "Linux Libertine O."

OK, but my question is: how do I do that?

The [manpage for mkfontdir]("http://manpages.ubuntu.com/manpages/karmic/man1/mkfontdir.1.html") explains about the fonts.alias file.  I have four files called that in my filesystem.  They are in:

/usr/share/fonts/X11/100dpi/
/usr/share/fonts/X11/75dpi/
/usr/share/fonts/X11/misc/
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/

To which of these files do I add the new alias?  Or do I create a new fonts.alias file?  If the latter, where do I put it?

Even after I get the alias into a file, I'm going to have to tell the X server to (re)read the file, right?  How do I do that?

I have found a few commands that look like they might do the job, but I don't want to mess with them blindly, since they are going to be run on system config files.

Can fc-cache do this?  Or fc-cat?  The command [update-fonts-alias]("http://manpages.ubuntu.com/manpages/dapper/man8/update-fonts-alias.8.html") certainly seems to be designed to do this, but I can't figure out from its man page how I'm supposed to make it work.  Also, I've seen references to the command  xset fp rehash, which also seems like it is designed to do just that.

Has anyone here done this before?  Can anyone give me a little guidance on how to get going on this?

Thanks

---

### Post by gldearman on 2009-07-14
OK, here is what I have tried so far.  It didn't work.  

In the file /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/fonts.alias, I added the following line:

```
"Linux Libertine" "-philipp poll-linux libertine-medium-r-normal--0-0-0-0-p-0-iso8859-1"
```

The first field is supposed to be the alias I am creating.  The second field is the XFLD name of the font "Linux Libertine O."  I got it from the file fonts.dir, in the same directory.

After that, I type:

```
sudo xset fp rehash
```

The command executes without any error messages, but the alias does not take.  All of my old documents written in Linux Libertine still are displayed in the system font (DejaVu Sans).

Can anyone tell me what I am doing wrong?

Thanks!

---

### Post by gldearman on 2009-07-14
Hi, all,

Even though no one here was able to help me, I was able to figure out the problem by myself.  I thought I ought to post the solution here in case someone searches the forum for this in the future.  Maybe this post will help somebody out.

To create the font alias, I created a file (as root) in the directory /etc/fonts/conf.d.  I called the file 30-fix-linux-libertine.conf (The filename has to conform to the pattern [0-9][0-9]*.conf; see the README file in that directory.)  This is what I put in the file:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "/etc/fonts/fonts.dtd">
<fontconfig>
<alias>
<family>Linux Libertine</family>
<accept><family>Linux Libertine O</family></accept>
</alias>
</fontconfig>
```

Then, I restarted.  Problem fixed.  I found this solution [here]("http://www.mail-archive.com/debian-desktop@lists.debian.org/msg02086.html").

Thanks to everyone who read my problem!

---

