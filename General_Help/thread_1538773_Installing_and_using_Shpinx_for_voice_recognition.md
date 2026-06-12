---
title: "Installing and using Shpinx for voice recognition"
date: 2010-07-25
forum: General Help
---

### Post by sideburns on 2010-07-25
We've tried installing Sphinx on my sister's Ubuntu computer, using Synaptic Package Manager, but nothing shows up on her menu, and searching for it brings up nothing.  What package do we need to install (Either through Package Manager or manually will do.) to get it working?

---

### Post by jerenept on 2010-07-25
PocketSphinx, or something right?

Maybe it is a command-line program?

---

### Post by sideburns on 2010-07-25
There is no such program listed in Package Manager and after installing the libraries and utilities, none shows up when we search for files containing the word sphinx.

---

### Post by jerenept on 2010-07-25
click "Reload" in Synaptic, then search again.

Is this a graphical program?

After you install pocketsphinx, run pocketsphinx-wsj.

I think that is it there. or you could check out CMU Sphinx on Sourceforge ([http://sourceforge.net/projects/cmusphinx/]("http://sourceforge.net/projects/cmusphinx/"))

---

### Post by sideburns on 2010-07-25
After reloading, I installed every file listed for pocketsphinx except the devel files.  There's still nothing on her menu and searching her file system for files containing "pocketsphinx" turns up nothing at all.  And, I might add, SourceForge only seems to offer Windows binaries.

---

### Post by sideburns on 2010-07-25
I have just checked on #cmusphinx, on irc.freenode.org, and pocketsphinx is not the appropriate program, as it's just a module to be added to other programs.

---

### Post by oaxacamatt1 on 2010-07-25
Hi Sideburns,
I have found that when running XFCE for XUbuntu that menu items do not always show up on the drop menu.  I believe that this is a limitation of XFCE.  

If you are running good ole' Ubuntu then simply search for pocketsphinx or sphinx find the directory where sphinx inhabits and then make yourself an icon on either the desktop or on the top panel.  Once you find the dir. for sphinx right click on the top panel and you can get an icon up there.  

Also I would suggest trying the CMU Sphinx website for a little Y-elp.
[http://cmusphinx.sourceforge.net/](http://cmusphinx.sourceforge.net/)
Good luck,  Let us know if you like it...
M

---

### Post by sideburns on 2010-07-25
Tell me something I didn't know twenty years ago.  I know how to make icons, but if there's no such program, it doesn't do any good, does it?  And, as I've already written, it's not the right program anyway.

---

### Post by sideburns on 2010-07-26
I've been playing with computers, off and on, since about 1968, and playing with them full time for fun and/or profit since the early 1980s.  Granted, I haven't done any programming in over a decade, but I do know my way around both Linux and Windows.

Not only did I RTFM, I went on the appropriate irc channel and got assistance from people who use the program every day.  They assured me that it's not the program my sister needs.

Now, if that's not enough to satisfy you, feel free to go off in a huff; if that's not good enough, make it a minute-and-a-huff.

The above is a reply to a post that has since been deleted as inappropriate.  If you don't know what it refers to, just ignore it.

---

### Post by DJonsson2008 on 2010-09-19
When I try to run pocketsphinx_wsj I get 

"Warning: Could not find Mic element"

How do I assign mic element in pocketsphinx?

---

### Post by DJonsson2008 on 2010-09-19
Note: I'm trying to use pocketsphinx_wsj
on 10.04 LTS

---

### Post by Froggus on 2010-09-25
Hi did anyone get this program working?

Sideburns, did you find a solution? I am looking for voice rec. system for use with ubuntu any help would be appreciated

Thanks

---

### Post by DJonsson2008 on 2010-09-25
Correct me if I'm wrong.

But I don't think sphinx or pocketsphinx, or Julius are fully developed. As they are toolkits for developers and experimenters more than anything else. 

Which makes me believe shouldn't they be better described in the repository description as such ie.?
[http://packages.ubuntu.com/karmic/python-pocketsphinx](http://packages.ubuntu.com/karmic/python-pocketsphinx)

The Sphinx and Julius documents and forums are not user friendly. Most of the online chatter about these packages seems to be on the "recompile and reprogram to make it work level".

I also wonder how these projects can gain critical mass without bridging the gap where more people can at least get their tools to a 'hello' level without 20-40 hours of configuring, programing, testing, and re-compiling. 

Anyhow "Simon" is a speech to text GUI that at least provides a graphical interface, installable from a .deb file that helps make sense of the components involved in making speech to text work. As well their forums and FAQs provide practical advice closer to a user friendly beginner level.

[http://simon-listens.org/](http://simon-listens.org/)

Speech to text is also explored here.
[http://ubuntuforums.org/showthread.php?t=1575877&highlight=speech+into+text](http://ubuntuforums.org/showthread.php?t=1575877&highlight=speech+into+text)

---

