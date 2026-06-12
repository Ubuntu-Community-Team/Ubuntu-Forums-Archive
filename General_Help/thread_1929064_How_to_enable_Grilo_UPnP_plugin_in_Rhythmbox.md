---
title: "How to enable Grilo UPnP plugin in Rhythmbox?"
date: 2012-02-21
forum: General Help
---

### Post by tellapu on 2012-02-21
The newest version of rhythmbox should have a Grilo UPnP plugin ([http://projects.gnome.org/rhythmbox/rhythmbox-2.95.news](http://projects.gnome.org/rhythmbox/rhythmbox-2.95.news)), but I can't find it in Rhythmbox and a way to enable it.
I installed rhythmbox 2.95 according to this instruction ([http://www.webupd8.org/2012/01/rhythmbox-finally-ported-to-gtk3.html](http://www.webupd8.org/2012/01/rhythmbox-finally-ported-to-gtk3.html)).
The rhythmbox-plugin-coherence ([http://coherence.beebits.net/wiki/RhythmBox](http://coherence.beebits.net/wiki/RhythmBox)) is not in the normal repositories (Ubuntu 11.10) anymore and so I thought it would be great to have the new rhythmbox version with pre-installed (?) Grilo plugin instead of installing from another repository or manually.

Or do I need to install the Grilo plugin with another repository (ppa:grilo-team/ppa) in Ubuntu ([https://live.gnome.org/Grilo](https://live.gnome.org/Grilo))? And add the plugin from there?
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by tellapu on 2012-02-26
Can anybody help? I would be very happy :D .
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by Frogs Hair on 2012-02-26
If the plug-in is installed properly it should appear on the list when you select Edit > Plug-ins. The PPA may be the best way to get the latest updates and no matter what method you use make sure the plug-in is compatible with the version of Ubuntu and Rythmbox in use .As you know Rythmbox is not the default player in 11.10.

---

### Post by tellapu on 2012-02-26
Dear Frogs Hair,

Thanks a lot for your reply! If I understand you right, I have to install the
grilo plugins (grilo-0.1-plugins) in addition to the new rhythmbox. 
Or should it come along with the new rhythmbox installation (through the ppa:webupd8team/rhythmbox)?

Well, I installed grilo-0.1-plugins (with some additional recommended
packages: libgrilo-0.1 (0.1.18-1~oneiric2), libgupnp-av-1.0-2
(0.8.0-2), libtracker-sparql-0.10-0 (0.10.24-1build2), libunistring0
(0.9.3-4)) from the ppa:grilo-team/ppa. Unfortunately there has not been an new
plugin (e.g. Grilo plugin) within rhythmbox (Edit > Plug-ins).

So I added grilo-0.1-tools, then gir1.0-grilo-0.1, but no effect neither.

How do I know whether the plug-ins are compatible with Ubuntu 11.10?

What next?

Cheers,

tellapu
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by tellapu on 2012-03-03
Bump!
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by tellapu on 2012-03-11
Well, it seems that nobody knows anything at the moment, probably it does not yet work ... The coherence plugin does not work anymore.
So I use ushare: Another quite stable solution for UPnP shares is the command line tool  uShare that also works independent of a running music player. After set  up with  

[LIST]
[*]   sudo dpkg-reconfigure ushare
[*]we can share any directory or multiple directory by running
  ushare -D --name=<name_of_my_stream> --content=<path_to_mediafiles>
[*]In case you are not so comfortable with the command line there is a GUI tool [stream2ip]("https://launchpad.net/stream2ip/+download") ([https://launchpad.net/stream2ip/+download](https://launchpad.net/stream2ip/+download)) that will do most of the work for you.
[/LIST]
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by rtg on 2012-04-04
Grilo plugin is not built as a part of Rhythmbox in Precise. The package needs to be modified for this.

I filed [LP:973295]("http://launchpad.net/bugs/973295") for this but Grilo is currently in Universe which may mean that it won't make it to Main (where rhythmbox-plugins are) until release.

---

### Post by tellapu on 2012-04-04
Thanks for your research and sharing your information. It is really sad that it seems the UPnP plugin does even not to work in 12.04 (Precise Pangolin). I hoped they will fix it with the new version. I emailed the developers of rhythmbox a while ago. :-(
[LEFT][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][/LEFT]

---

### Post by rtg on 2012-04-04
It is not the rhythmbox developers' fault but a packaging issue. Visualisation plugin is also not being built as it uses libmx which is in Universe.

Anyway, rhythmbox 2.96-0ubuntu4~lp973295 is currently being built in my testing PPA at [ppa:rye/testing]("https://launchpad.net/~rye/+archive/testing") where rhythmbox-plugins package will include Grilo plugin, so feel free to test it.

---

### Post by tellapu on 2012-04-04
Hi rtg!
Thanks for the clarification. Are you in the rhythmbox team? 
I tried to contact them but never received an answer ... Hopefully the packaging issue can be solved.
Thanks for the testing-ppa-offer, at the moment I won't have time to try it, perhaps when I have installed Ubuntu 12.04, I will give it a try.
Thx anyway.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by sindbad6 on 2012-06-07
Hello rtg,

is it possible, that you add a ppa for the new pangolin ubuntu 12.04? I would be very interested to add UPnP capability to rhythmbox.

Thanks in advance.

Sindbad6

---

### Post by tellapu on 2012-06-18
Hi sinbad6! Just try it. rtg has not been posting for a while, it is a pity.

Unfortunately I have not seen any sign of UPnP in rhythmbox 2.96 in Ubuntu 12.04 :-( .

Is there hope for the hopeless?
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by billstei on 2012-07-14
I have the grilo plugin working in Ubuntu 12.04 (the plugin seems to have some issues/bugs, but I have not tried newer versions...) and here is what I did:

sudo apt-get build-dep rhythmbox

Get rhythmbox source code 2.96 from here: [http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/2.96/](http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/2.96/)

Extract the rhythmbox-2.96.tar.xz file and go into that folder.

./configure

Clear up any errors the configure complains about, and repeat ./configure as many times as necessary to get a good configure.

make

There are two files: grilo.plugin and libgrilo.so -- to see these do:

cd grilo
ls
ls .libs

I did not use make install at this point, I just created a folder in the existing rhythmbox installation, and put both files in that folder:

sudo mkdir /usr/lib/rhythmbox/plugins/grilo
sudo cp grilo.plugin /usr/lib/rhtythmbox/plugins/grilo/
sudo cp .libs/libgrilo.so /usr/lib/rhythmbox/plugins/grilo/

Check to see that the two files are there:

ls /usr/lib/rhythmbox/plugins/grilo

You may want to run rhythmbox at first from a terminal in order to monitor any error messages, then in RhythmBox menu Edit -> Plugins -> Grilo media browser, check it.  My DLNA server name (via minidlna) is listed in the Shared section of the RhythmBox browser window pane.

The only issue I am having with it is if I stop using it and stream from some other source in RhythmBox, and then come back to it, it hangs and won't browse anymore.  If I Quit out of RhythmBox and come back in it works again.

---

### Post by m3topaz on 2012-07-15
I'm using a pretty clean install of Precise (3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux) on a Macbook 2,1. Rhythmbox 'sees' my DLNA server which is a MyBookLive with "Public" shares of music enabled - the device appears in the Shared list in the left hand pane of Rhythmbox.
It works just fine (apart from if you bash it hard!)
I checked for plugins with
$ sudo apt-cache policy coherence* and $ sudo apt-cache policy grilo*
- nothing is installed.
Maybe Rhythmbox 'just works' with DLNA devices out of the box on Precise? I'd be curious to know why though!

---

### Post by tellapu on 2012-07-23
@billstei: Thanks for the instructions. Did you uninstall the default rhythmbox 2.96 of Ubuntu 12.04?
I hoped I can download the source and transfer only the plugin, but you need to build/configure the plugin as well ...

@m3topaz: That is really interesting. Do you see a plugin grilo, any UPnP/DLNA configuration possibility?

I have upgraded to rhythmbox 2.97 via PPA, but no UPnP/DLNA configuration seen.[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by billstei on 2012-07-24
I am using RhythmBox 2.96 and the issue I noted above might have been with MiniDLNA, because when I tried PS3MediaServer I did not have the same trouble browsing.

---

### Post by tellapu on 2012-07-25
@billstei: Thanks for the update. Did you uninstall the default rhythmbox 2.96 of Ubuntu 12.04?
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by billstei on 2012-07-25
@tellapu - I have not changed the default install of Rhythmbox 2.96 in Ubuntu 12.04 or uninstalled it, other than adding the plugin directory/files as noted above.

---

### Post by tellapu on 2012-11-30
This is even easier:
[http://bernaerts.dyndns.org/linux/240-ubuntu-precise-upnp-dlna-client](http://bernaerts.dyndns.org/linux/240-ubuntu-precise-upnp-dlna-client)

It worked for me. Although I just realized that it does not share the rhythmbox data to other UPnP/DLNA clients, but rather to play play music from other uPnP sources. Sayang![LEFT][COLOR=#000000][/COLOR][/LEFT]

---

