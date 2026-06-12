---
title: "Application that plays single rar files containing mp3 files"
date: 2011-05-21
forum: General Help
---

### Post by dumpster25 on 2011-05-21
Anybody knows about a media player for Ubuntu that plays mp3 files inside an existing rar file?

On Windows I've been using XMPlayer for that purpose. XMPlayer has got a rar plugin and it works as expected.

I stumbled across this plugin for Audacious but I'm not sure it's related
[http://kittylambda.com/rsn_plugin_for_audacious](http://kittylambda.com/rsn_plugin_for_audacious)

I've ran XMPlay succesfully with wine with the rar plugin and it actually works (a bit slower but it works). But what I'm missing is integration with nautilus since drag and drop won't work from nautilus to XMPlayer. 

I have to navigate to the rar file manually on the file-open window and since Nautilus puts it's mounts on /home/[username]/.gvfs
it's a bit cumbersome.

I'd appreciate if anyone could tell me if there's a native application that does this on Ubuntu. Thanks in advance :D

---

### Post by inameiname on 2011-05-21
Here's a similar thread about this:

[http://ubuntuforums.org/showthread.php?t=308015](http://ubuntuforums.org/showthread.php?t=308015)

Doesn't really help, I know, but it shows there are others with same question. I am curious myself.

---

### Post by ivanovnegro on 2011-05-21
Actually yes there is an application, the newest version of the media player called [DeaDBeeF]("http://deadbeef.sourceforge.net/"). Now it can play also rar files just like Foobar.
But Im a little bit confused about your question because VLC can also do the same and even SMPlayer.

Edit: Or maybe Im understanding it wrong that there is the possibility to play zip files. Not sure.

---

### Post by dumpster25 on 2011-05-21
> **ivanovnegro said:**
> Actually yes there is an application, the newest version of the media player called [DeaDBeeF]("http://deadbeef.sourceforge.net/"). Now it can play also rar files just like Foobar.
But Im a little bit confused about your question because VLC can also do the same and even SMPlayer.

Edit: Or maybe Im understanding it wrong that there is the possibility to play zip files. Not sure.

I tried VLC and SMPlayer before creating the thread. It works only with video files inside a rarfile but not with mp3files.

Thanks I'll definitely give DeaDBeef a shot :)

---

### Post by ivanovnegro on 2011-05-21
> **dumpster25 said:**
> I tried VLC and SMPlayer before creating the thread. It works only with video files inside a rarfile but not with mp3files.

Thanks I'll definitely give DeaDBeef a shot :)

So, I think DeaDBeef should work.

---

### Post by dumpster25 on 2011-05-21
I tried DeaDBeef. It only managed to play from zipfiles but unfortunately no rarfiles. 

Bummer :|

I can live with XMPlay through wine for now.

DeadBeef seemed speedy though. Even though I dled the static version.
ivanovnegro, have you tried DeaDBeef with rar files?

---

### Post by ivanovnegro on 2011-05-21
Actually not tried it with rar files, so you must be right if its not working.
You could propose that to the developer?
DeaDBeef is a speedy and very decent audio player with a superb sound quality, dont forget audio player not a jukebox, I admit the name is horrible. :)

---

### Post by dumpster25 on 2011-05-21
I read this on the project's support page:

[http://sourceforge.net/tracker/index.php?func=detail&aid=2934177&group_id=272657&atid=1159089](http://sourceforge.net/tracker/index.php?func=detail&aid=2934177&group_id=272657&atid=1159089)

> there's now support for archive plugins, via VFS plugins, and zip support
 is already working in 0.5

 other formats will follow with time.

It's a matter of waiting then :)

---

### Post by ivanovnegro on 2011-05-21
> **dumpster25 said:**
> I read this on the project's support page:

[http://sourceforge.net/tracker/index.php?func=detail&aid=2934177&group_id=272657&atid=1159089](http://sourceforge.net/tracker/index.php?func=detail&aid=2934177&group_id=272657&atid=1159089)



It's a matter of waiting then :)

That sounds promising and Im sure it will be implemented. The development is relativeley fast anyway.

---

### Post by Vaphell on 2011-05-21
can't you write some script to unrar your audio stuff and pack it in zip format?

---

### Post by dumpster25 on 2011-05-22
> **Vaphell said:**
> can't you write some script to unrar your audio stuff and pack it in zip format?

I could definitely. But that would be a step backwards in my opinion.

---

