---
title: "sipie issues"
date: 2009-11-16
forum: General Help
---

### Post by nixIT on 2009-11-16
Hello all,

Is there anyone out there using sipie?  I have been using sipie with very minimal problems, until today.  When I launched cliSipie today, I am greeted with this:

```

~$ cliSipie
/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/Config.py:12: DeprecationWarning: the md5 module is deprecated; use hashlib instead
Login Error token not found:, see Auth-ERROR.html
Traceback (most recent call last):
  File "/usr/local/bin/cliSipie", line 8, in <module>
    load_entry_point('Sipie==0.1196144357', 'console_scripts', 'cliSipie')()
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 376, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 212, in auth
Sipie.Factory.LoginError

```

I thought maybe my config file got corrupted, so I deleted it and sipie walked me through asking username, country, etc.  

Any ideas what is causing this?  Is sipie working today for anyone?

--nixIT

---

### Post by blueridgedog on 2009-11-16
The error is advising you that your python file, /usr/local/bin/cliSipie is calling a module that is no longer supported by the version of python that is loaded on your system, as cliSipie is calling for the md5 module and they recommend and insist on using the hashlib module.

The Sipie website has a version dated March of 2008.  Is that the one you are using?

If you have the latest version, you can try an email to one of the developers via their sourceforge accounts.

---

### Post by aldogger on 2009-11-17
I am having the same problem.  Sipie was working fine till this week.  That DepreciationWarning has always been there it is not new, nor the cause of the Auth-Error message.  Anyone else having this problem?

```

~$ sipie.py
/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/Config.py:12: DeprecationWarning: the md5 module is deprecated; use hashlib instead
Login Error token not found:, see Auth-ERROR.html
Login Error token not found:, see Auth-ERROR.html
Login Error token not found:, see Auth-ERROR.html
Traceback (most recent call last):
  File "/usr/local/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1196144357', 'sipie.py')
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/EGG-INFO/scripts/sipie.py", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 376, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 212, in auth
Sipie.Factory.LoginError
```

I also attempted to remove everything in ~/.sipie/ and reconfigure to no avail.

---

### Post by nixIT on 2009-11-17
> **blueridgedog said:**
> The error is advising you that your python file, /usr/local/bin/cliSipie is calling a module that is no longer supported by the version of python that is loaded on your system, as cliSipie is calling for the md5 module and they recommend and insist on using the hashlib module.

The Sipie website has a version dated March of 2008.  Is that the one you are using?

If you have the latest version, you can try an email to one of the developers via their sourceforge accounts.

Sipie was working fine until yesterday.  I've always received the md5 deprecated warning, and it still worked.  

I don't know if this is a Sipie, Ubuntu, Linux, or sirius problem.

--nixIT

---

### Post by aldogger on 2009-11-17
My uSirius also quit working this week, I was reading on the Blackberry Forums that it looks like Sirius moved their Internet streaming over to the XM servers.

---

### Post by aldogger on 2009-11-17
[http://forums.crackberry.com/f35/usirius-not-logging-364702/](http://forums.crackberry.com/f35/usirius-not-logging-364702/)

---

### Post by aldogger on 2009-11-17
[http://www.digitalradiocentral.com/sir-xmro-internet-radio/7978-sirius-com-apparently-changes-login-code-3rd-party-players-now-broken.html](http://www.digitalradiocentral.com/sir-xmro-internet-radio/7978-sirius-com-apparently-changes-login-code-3rd-party-players-now-broken.html)

---

### Post by nixIT on 2009-11-17
> **aldogger said:**
> [http://www.digitalradiocentral.com/sir-xmro-internet-radio/7978-sirius-com-apparently-changes-login-code-3rd-party-players-now-broken.html](http://www.digitalradiocentral.com/sir-xmro-internet-radio/7978-sirius-com-apparently-changes-login-code-3rd-party-players-now-broken.html)

Thanks for the update on this.  What a p1sser.  :(  work just isn't the same without the ability to stream sirius.  

--nixIT

---

### Post by aldogger on 2009-11-17
yeah, sux, I was using uSirius to stream through my Blackberry.  uSirius has a huge following so hopefully someone picks it up and figures it out.    As far as sipie goes, I know there is a way to get VLC media player to work on Firefox through the Sirius online linstening function.  Ill play with that to see if I can get it working today.

---

### Post by aldogger on 2009-11-17
Looks like the Sirius Player is working.  I have MPlayer plugin installed, and streaming is working off the "Listen Online" through Firefox.  Would rather have my sipie but this works.  (it took a while for the player to connect, just be patient; if firefox prompts you to install a missing plugin, install the Mplayer plugin).

---

### Post by nixIT on 2009-11-17
> **nixIT said:**
> Thanks for the update on this.  What a p1sser.  :(  work just isn't the same without the ability to stream sirius.  

--nixIT

Ok, I can log in normally to the sirius website and stream music that way.  But nothing beats loading up a CLI and running cliSipie.  I wonder what could be going on if I can stream through their website but not with sipie.

--nixIT.

---

### Post by nixIT on 2009-11-17
Here is some more info, as I've been looking at this randomly throughout the day. 

the current address, that allows sirius to play through their website is:

```

http://www.sirius.com/player/listen/play.action?channelKey=hairnation&genreKey=rockSIR&categoryKey=music&stopped=no

```

does anyone know what URL sipie uses for the streaming?

--nixIT

---

### Post by nixIT on 2009-11-20
FYI,

Eli is in the process of fixing Sipie, and has made some changes to Sipie on sourceforge that will allow cliSipie to work.  So if you are having problems, which we are, head over there to grab the changed files.

Only question is, how do I get the new files to work?

--nixIT

---

### Post by nixIT on 2009-12-09
it appears there is a new version checked into subversion on sourceforge.  However, I am unsure how to get that working.

Has anyone checked out the new (sub)version from sourceforge and got sipie working again?

--nixIT

---

### Post by stephanunc on 2010-02-10
I'm also unable to get the new version working. Do i have to uninstall the previous version somehow? Did you get it working? 

I followed instructions on [https://sourceforge.net/projects/sipie/forums/forum/697500/topic/3465398/index/page/2](https://sourceforge.net/projects/sipie/forums/forum/697500/topic/3465398/index/page/2)

Thanks.

---

### Post by nixIT on 2010-02-24
have not gotten it working.  There are many things with my linux distros that stop working and I can't get them going again.  :(

---

