---
title: "Conky Transmission Python Script"
date: 2010-12-08
forum: General Help
---

### Post by kaivalagi on 2010-12-08
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]


**_[SIZE="3"][COLOR="Blue"]Intro[/COLOR][/SIZE]_**

This is a simple script to display what is current downloading in Transmission. The script talks to Transmission using rpc via the python-transmissionrpc package and allows templates...

This script requires Transmission (daemon) to be installed and running, with the rpc authentication requirement set to false, edit the /etc/transmission-daemon/settings.json file to set the rpc auth requirement to "false" when the daemon is stopped then reload and start it. Step by step instructions are in the "gotchas" section below.

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conky<scriptname>/

**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the script: 

```
sudo apt-get update && sudo apt-get install conkytransmission
```

**[COLOR="Blue"]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyTransmission script to point to the correct location where conkyTransmission.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE="3"][COLOR="Blue"]Usage Help[/COLOR][/SIZE]_**

To use the script in conky in it's simplist form, you'll need an exec statement like this:

```
${exec conkyTransmission}
```

To use a template for custom output, I suggest you read the README attached, and take a look at the example conkyrc and template files that are installed to "/usr/share/conkytransmission/example".

You can get the current help options at any time by running:

```

conkyTransmission -h

```

or

```

conkyTransmission --help

```

```
Usage: conkyTransmission [options]
Options:
  -h, --help            show this help message and exit
  -s SERVER, --server=SERVER
                        [default: 127.0.0.1] The server to connect to where
                        the transmission daemon is running
  -p PORT, --port=PORT  [default: 9091] The port to connect to where the
                        transmission daemon is running
  -U USERNAME, --username=USERNAME
                        [default: ] Username to use when connecting
  -P PASSWORD, --password=PASSWORD
                        [default: ] Password to use when connecting
  -S, --showsummary     Display summary output. This is affected by the
                        --activeonly option.
  -H, --hidetorrentdetail
                        Hide torrent detail output, if used no torrent details
                        are output.
  -t FILE, --torrenttemplate=FILE
                        Template file determining the format for each torrent.
                        Use the following placeholders: [name], [state],
                        [totaldone], [totalsize], [progress], [nofiles],
                        [downloadrate], [uploadrate], [eta], [currentpeers],
                        [currentseeds], [totalpeers], [totalseeds], [ratio].
  -T FILE, --summarytemplate=FILE
                        Template file determining the format for summary
                        output. Use the following placeholders: [notorrents],
                        [totalprogress], [totaldone], [totalsize],
                        [totaldownloadrate], [totaluploadrate], [totaleta],
                        [currentpeers], [currentseeds], [totalpeers],
                        [totalseeds], [totalratio].
  -a, --activeonly      If set only info for torrents in an active state will
                        be displayed.
  -l NUMBER, --limit=NUMBER
                        [default: 0] Define the maximum number of torrents to
                        display, zero means no limit.
  -b SORTTYPE, --sortby=SORTTYPE
                        Define the sort method for output, can be "progress",
                        "queue", "eta", "download", "upload" and "ratio". Also
                        note that a torrent's state supersedes anything else
                        for sorting, in the order, from top to bottom:
                        downloading, seeding, queued, paused, unknown)
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

**_[SIZE="3"][COLOR="Blue"]Gotchas[/COLOR][/SIZE]_**

1) As mentioned in the initial blurb at the top this script uses transmissions RPC interface to get details of torrents. However to overcome permissions issues is will probably be necessary to edit the transmission daemon settings file so that RPC does not require any authentication. This shouldn't pose any security issues as routers/firewall defaults should cover that off.

I did the following to get it working in Ubuntu:

**Step 1** - Stop the Transmission daemon and open the settings file for editing:

```
sudo /etc/init.d/transmission-daemon stop
gksudo gedit sudo /etc/transmission-daemon/settings.json &
```

**Step 2** - Make the changes to the settings, edit this line:

```
    "rpc-authentication-required": **[COLOR="Red"]true[/COLOR]**,
```

to be this:

```
    "rpc-authentication-required": **[COLOR="Green"]false[/COLOR]**,
```

**Step 3** - Close the file then reload and start the daemon 
```
sudo /etc/init.d/transmission-daemon reload
sudo /etc/init.d/transmission-daemon start
```

2) Conky has a default limitation of 128 bytes for any text output from a variable (such as execi). If you are creating large templates with more characters than the default buffer size can handle, the output will get truncated. If this happens you can override the default behaviour by setting as new buffer size before the TEXT section in your conkyrc file, as follows:

```

text_buffer_size 1024

```


**_[SIZE="3"][COLOR="Blue"]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkytransmission"]https://code.launchpad.net/~conky-companions/+junk/conkytransmission
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by kaivalagi on 2010-12-14
**[COLOR="Red"][SIZE="3"]IMPORTANT NEWS[/SIZE][/COLOR]**

All the script packages have now been copied into the **Conky Companions PPA**. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this: 

```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*

```
Then follow the modified first post instructions for the scripts

[COLOR="Red"]**Script updates will only be published through this new ppa going forwards**[/COLOR]

---

### Post by kaivalagi on 2011-01-04
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated to not display anything at all when nothing is available rather than the previous 'No torrent info to display' message'
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkytransmission_1.02_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkytransmission_1.02_source.changes)

The apt packages should be available soon

---

### Post by snkiz on 2011-01-17
Hi k, glad to see the move to transmission! and I see you recycled some code ;)

Since Transmission recently gained the client/server model I was looking for. (albeit only with the qt client.) I hoping this would come. But I got few bugs for ya.

[https://bugs.launchpad.net/conkytransmission/+bug/704212]("https://bugs.launchpad.net/conkytransmission/+bug/704212")
As you've said your aware of this already, just a friendly reminder that it matters.

[https://bugs.launchpad.net/conkytransmission/+bug/704192]("https://bugs.launchpad.net/conkytransmission/+bug/704192")
Ratios show twelve decimal places?

[https://bugs.launchpad.net/conkytransmission/+bug/704200]("https://bugs.launchpad.net/conkytransmission/+bug/704200")
The eta time format is strange for per torrent info.

[https://bugs.launchpad.net/conkytransmission/+bug/704203]("https://bugs.launchpad.net/conkytransmission/+bug/704203")
Appears to be some missing data. I'm sure you'll get it sorted out, this is a new script after all.

and Lastly
[https://bugs.launchpad.net/conkytransmission/+bug/622219]("https://bugs.launchpad.net/conkytransmission/+bug/622219")
Not sure how your going to pull this one off, but I have the upmost confidence in you. ;)

As always great work K. Seems you've got a real project on your hands now.

Cheers!

---

### Post by kaivalagi on 2011-01-18
Updated the bugs although you did assign them to the conkytransmission project which isn't anything to do with me...conky companions is the PPA and code repo

New version of the script will be available soon for the rounding of ratio output but as detailed in the bugs the other stuff can't be sorted.
[LIST]
[*]The eta output is as designed and comes from transmission where the first digit is the number of days. This will remain as is.
[*]The peer and seed counts aren't available in the transmission rpc module which is what's used. If they become available and I know about it then you'll see them.
[*]The file count looks like a bug with the rpc module not providing file information at all.
[/LIST]

---

### Post by snkiz on 2011-01-18
I didn't see a bug tracker for conky companions. So I just searched against the package. Its not yours? now I'm confused. 

Anyhow thanks for the clarification. I was thinking since transmission is actually using its rpc for the web and qt clients, that the same info would be available to python. According to the link you provided, the python module doesn't yet implement all of the spec.

---

### Post by kaivalagi on 2011-01-18
> **snkiz said:**
> According to the link you provided, the python module doesn't yet implement all of the spec.
Indeed, I could rip the guts of the module and make it my own and add additional methods but I want to keep things simple...

---

### Post by kaivalagi on 2011-01-18
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Thought I better post the standard update post...

Updates as follows:
[LIST]
[*]Updated to limit ratio to 2 decimal places
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkytransmission_1.03_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkytransmission_1.03_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2011-01-18
Snkiz

I noticed the bug raised for rpc...I had to set this in my ~/.config/transmission-daemon/settings.json file:

```
"rpc-authentication-required": false,
```

I remote in to my PC from my phone to manage my torrents no probs that way

Hope that helps

---

### Post by snkiz on 2011-01-18
It does, I'm paranoid.

---

### Post by kaivalagi on 2011-01-19
Just looking through the rpc module code I found indications of protocol versions meaning differing functionality in transmissionrpc/client.py:

```
        if method == 'torrent-get':
            for item in data['arguments']['torrents']:
                results[item['id']] = Torrent(self, item)
                if self.protocol_version == 2 and 'peers' not in item:
                    self.protocol_version = 1
```

Looks like for peer info we would need version 2 minimum (as peers "might" be there it seems), but I haven't found out what version my transmission runs with as yet..if you have more time than me maybe you can make sense of this somehow?

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by sbjaved on 2012-02-15
Hi, I'm running Fedora and I love your script. I wanted to ask you is there any possible reason that Transmission would stop downloading torrents after installing transmission-daemon? Because mine does! 

I installed transmissionrpc from source (since I couldn't find any package for Fedora) and didn't change and settings in the daemon's json file (rpcauthentication was already set to false). The daemon was up & running. The script's verbose output spat out no errors except "no torrents found". But the torrent I added in Transmission wouldn't download and was stuck at 0% @ 0kbps (it was an ubuntu-12.04 torrent so it was well seeded).

The moment I yum removed the daemon, Transmission started working like there was no problem. I would very much appreciate any help because I love your scripts :) (im already running conkyGoogleReader). Thanks!

---

