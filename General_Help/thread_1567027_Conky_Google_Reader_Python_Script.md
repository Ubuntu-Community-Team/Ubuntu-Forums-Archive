---
title: "Conky Google Reader Python Script"
date: 2010-09-03
forum: General Help
---

### Post by kaivalagi on 2010-09-03
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

[COLOR="Blue"]_**[SIZE="4"]Intro[/SIZE]**_[/COLOR]

I have put together this python script to output Google Reader feed details from a users google reader setup, for use in Conky. 

Some key features
[LIST]
[*]Utilises the experimental Google Reader API.
[*]Supports the use of a template to define the layout of feed info, both individual feed and summary data
[/LIST]

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conky<scriptname>/

Hope some of you find it useful

Any suggestions, please speak up!

**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the script: 

```
sudo apt-get update && sudo apt-get install conkygooglereader

```

**[COLOR="Blue"]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyGoogleReader script to point to the correct location where conkyGoogleReader.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


[COLOR="Blue"]_**[SIZE="4"]Usage Help[/SIZE]**_[/COLOR]

You can get the current help options at any time by running (change the path as necessary):

```
python ~/.scripts/conkyGoogleReader.py -h
```

or

```
python ~/.scripts/conkyGoogleReader.py --help
```

The usage is as follows:

```
Usage: conkyGoogleReader [options]
Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        username to login with
  -p PASSWORD, --password=PASSWORD
                        Password to login with, if not set the username is
                        used to fetch a 'conky' password from the keyring
  -t FILE, --template=FILE
                        Template file determining the format for each rss feed
                        summary. Use the following placeholders:
                        [unreadcount], [name], [url]
  -s FILE, --summarytemplate=FILE
                        Template file determining the format for summary
                        output. Use the following placeholders:
                        [totalfeedscount], [unreadfeedscount],
                        [unreadfeeditemscount]
  -S, --summaryoutput   Request summary output rather than each feeds details
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur.
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```


The important thing to note now is that the script is called using this in Conky. An example of use for standard output would be:
```
${execi 1800 conkyGoogleReader -u username@gmail.com -p password}
```

And for a summary:
```
${execi 1800 conkyGoogleReader -u username@gmail.com -p password -S}
```

If templates are used their options would be added to the above appropriately.

[COLOR="Blue"]_**[SIZE="4"]Development History[/SIZE]**_[/COLOR]

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkygooglereader"]https://code.launchpad.net/~conky-companions/+junk/conkygooglereader
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by etescartz on 2010-09-03
Hi! I just noticed something. I don't know if it's a bug or a typo. I'm using -S option and the output is:
```
2174 unread feed items, 161/3837 feeds have unread content.
```  The fact is,  that my total feeds count in Google Reader is just 641. How can i fix this?

---

### Post by VastOne on 2010-09-03
I keep getting "A username and/or password was not given!"

I am sure I have the syntax wrong starting it.

Can I get an example of what it should look like?

I have tried 

```
${execi 1800 conkyGoogleReader xxxxxx xxxxxx}
```
and
```
${execi 1800 conkyGoogleReader -u xxxxxx -p xxxxx}
```
and
```
${execi 1800 conkyGoogleReader -u=xxxxxx -p=xxxxxxx}
```

all with the same results

Thanks

---

### Post by kaivalagi on 2010-09-03
Second one i.e.:
```
${execi 1800 conkyGoogleReader -u username@gmail.com -p password}
```

Google reader is a user based tool as are all google tools, so it implies you need to login with your google username and password. All options if setup and used properly in Linux are short or long, short in the form "-a" or "-b setting" and long in the form "--alonger" or "--blonger=setting".

I've updated the first post to give a better example of use anyway :)

---

### Post by kaivalagi on 2010-09-03
> **etescartz said:**
> Hi! I just noticed something. I don't know if it's a bug or a typo. I'm using -S option and the output is:
```
2174 unread feed items, 161/3837 feeds have unread content.
```  The fact is,  that my total feeds count in Google Reader is just 641. How can i fix this?

Sounds like a bug to me, but I don't have this issue. I think it may relate to the particular feeds you have...not something easy to test or fault find for...

If you could setup a gmail account with these feeds or atleast to have the same behaviour and then pass on the credentials via PM I could then figure it out

---

### Post by VastOne on 2010-09-03
> **kaivalagi said:**
> Second one i.e.:
```
${execi 1800 conkyGoogleReader -u username@gmail.com -p password}
```

Google reader is a user based tool as are all google tools, so it implies you need to login with your google username and password. All options if setup and used properly in Linux are short or long, short in the form "-a" or "-b setting" and long in the form "--alonger" or "--blonger=setting".

I've updated the first post to give a better example of use anyway :)

Thanks K - :p

Looks and works great ~ !

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglereader_1.05_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglereader_1.05_source.changes)

The apt packages should be available soon

Cheers

**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by kaivalagi on 2010-11-21
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to dynamically call the available python exec as /usr/bin/python is linked to Python 3 (Arch) or will be at some point (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglereader_1.06_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkygooglereader_1.06_source.changes)

The apt packages should be available soon

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

### Post by Pat11111111 on 2011-01-22
Hello,

Thanks for this script. It is very useful.

However, I found a small bug (a copy/paste ;)) on line 107 of the conkyGoogleReader.py file (v. 1.06).

This line is part of the summary template file content loading.
This section is written as this:
```
# load the template file contents
    try:
        #fileinput = open(self.options.template)
        fileinput = codecs.open(os.path.expanduser(self.options.summarytemplate), encoding='utf-8')
        [COLOR="Red"]template = fileinput.read()[/COLOR]
        fileinput.close()
        # lose the final "\n" which should always be there...
        summarytemplate = summarytemplate[0:len(summarytemplate)-1]
    except:
        self.logError("Template file no found!")
        sys.exit(2)
```

Unfortunately this does not work. When I try to use a summary template file, I always have the ERROR message telling that the file is not found.

Here is the correct syntax. Simply use the summarytemplate variable instead of the template one...
```
# load the template file contents
    try:
        #fileinput = open(self.options.template)
        fileinput = codecs.open(os.path.expanduser(self.options.summarytemplate), encoding='utf-8')
        [COLOR="Red"]summarytemplate = fileinput.read()[/COLOR]
        fileinput.close()
        # lose the final "\n" which should always be there...
        summarytemplate = summarytemplate[0:len(summarytemplate)-1]
    except:
        self.logError("Template file no found!")
        sys.exit(2)
```

---

### Post by kaivalagi on 2011-01-23
Thanks pat, obvious bug now you've pointed it out...I wouldn't have seen it otherwise :) Fixed and will be released soonish or when other changes are needed too

---

### Post by kaivalagi on 2011-01-23
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Fixed bug stopping the loading of a custom summary template
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglereader_1.07_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglereader_1.07_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2011-02-26
**[COLOR=Green][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added keyring functionality so no clear text passwords need to be used, use the conkyKeyring tool to set passwords 
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglereader_1.08_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkygooglereader_1.08_source.changes)

The apt packages should be available soon


[SIZE="3"]**Hints and Tips**[/SIZE]

Here's the help from conkyKeyring:
```
Usage: conkyKeyring [options]

Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        The username where the password will be stored
                        against, this is usually an email address or other
                        account identifier which is used for login purposes
  -p PASSWORD, --password=PASSWORD
                        The password to be stored safely, leave unset to
                        retrieve the password
  -d, --delete          If set the password associated with the username given
                        is deleted
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

As an example I setup my gmail account first off by assigning a password to it like so:

```
conkyKeyring -u USER@gmail.com -p PASSWORD
```

I then use the reader script to get the feed details as follows:

```
conkyGoogleReader -u USER@gmail.com
```

If no -p/--password argument is given the password is expected to be in the keyring and an attempt to retrieve it is made...

Thanks to donoterase for getting the ball rolling with the email script, I hope my choice of approach works for everyone

Chimo

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by VastOne on 2011-05-13
Hey Mark!

I am using #! now and have run into a road block...

I keep getting the following when trying to run conkygooglereader

```
/usr/bin/env: python2: No such file or directory
```

I have the ppa, keyring and the reader all loaded by method one from this thread and Sector11's awesome thread on the #! forum

I have googled it but the remedies make no sense to me... I am in need of your expertise..

Thanks

CHIMO!

EDIT

I found it 8 messages up....

```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

I knew it sounded familiar...!

---

### Post by kaivalagi on 2011-05-14
you got it sorted...yeah python2 support is flaky in general these days. I tend to ensure the default "python" sym link points to python2/python2.6/python2.7 rather than python3 anyway...otherwise lots of my utilities / apps from other authors break

---

### Post by Ex Nihilo on 2011-06-13
Hi kaivalagi

I'm having some issues, using the --summarytemplate option with conkyGoogleReader.

It seems that no matter what summarytemplate I set, it always uses the default template (not the default summarytemplate).

My goal is just to print the unreadfeeditemscount, so I basically created a template file containing just [unreadfeeditemscount] and call it with the -s FILE option.
So am I doing something wrong?

I temporarly fixed it by changing the default string for summarytemplate in the conkyGoogleReder.py file and using the -S option, but I guess it is not the best thing to do.

Any suggestions?

Many thanks (also for all the great job you make on all these conkyStuff scripts)

---

### Post by kaivalagi on 2011-06-13
> **Ex Nihilo said:**
> Hi kaivalagi

I'm having some issues, using the --summarytemplate option with conkyGoogleReader.

It seems that no matter what summarytemplate I set, it always uses the default template (not the default summarytemplate).

My goal is just to print the unreadfeeditemscount, so I basically created a template file containing just [unreadfeeditemscount] and call it with the -s FILE option.
So am I doing something wrong?

I temporarly fixed it by changing the default string for summarytemplate in the conkyGoogleReder.py file and using the -S option, but I guess it is not the best thing to do.

Any suggestions?

Many thanks (also for all the great job you make on all these conkyStuff scripts)

Mmmmm, might be best to provide exactly what your command options are....I suspect that you need to call it like this:

```
conkyGoogleReader -u <USER> -p <PASSWORD> -s /path/to/summary/template**[COLOR="Red"] -S[/COLOR]**
```

Note the -S / --summaryoutput option, from the --help output:

```
-S, --summaryoutput   Request summary output rather than each feeds details
```

You need to tell the script you want summary data rather than a breakdown of the feeds

Here's the output for me of the command with the --verbose option added, the template file is just [unreadfeeditemscount] inside it:
```
 [USER@SYSTEM ~]$ conkyGoogleReader -u <USER> -p <PASSWORD> -s /tmp/summary.template -S --verbose
username: <USER>
password: <PASSWORD>
template: None
summarytemplate: /tmp/summary.template
summaryoutput: True
verbose: True
INFO: Initialising google reader...
INFO: Processing output...
3312
```

I've got lots to read!

Hope that helps

---

### Post by Ex Nihilo on 2011-06-13
Awesome !

You're right, that's what I didn't get. I was indeed calling
```
conkyGoogleReader -u <USER> -p <PASSWORD> -s /path/to/summary/template
```rather than
```
conkyGoogleReader -u <USER> -p <PASSWORD> -s /path/to/summary/template**[COLOR=Red] -S[/COLOR]**
```So it works perfectly now.
Thanks for the very fast answer ! :p

---

### Post by sbjaved on 2012-02-13
I'm getting this weird problem. The script runs fine in terminal. But it doesn't show up in conky. Here is my conky line:
${execpi 180 /home/saad/Downloads/src/conkyGoogleReader}

I added the commandline parameters (username etc) to the script itself. When I run "sh conkyGoogleReader" in terminal it outputs fine.

---

### Post by sbjaved on 2012-02-13
Okay. Found the problem! 
> #!/bin/bash
# cd /usr/share/conkygooglereader/

if [ -f /usr/bin/python2 ]; then
	pythoncmd="/usr/bin/python2"
elif [ -f /usr/bin/python2.7 ] ; then
	pythoncmd="/usr/bin/python2.7"
elif [ -f /usr/bin/python2.6 ] ; then
	pythoncmd="/usr/bin/python2.6"
else
	# here's hoping!
	pythoncmd="/usr/bin/python"
fi

pythonfile="/home/saad/Downloads/src/conkyGoogleReader.py -c 30 -u [email]xxxxx@gmail.com[/email] -p xxxxx -s /home/saad/Downloads/src/unread.template -S"

exec $pythoncmd $pythonfile **"$@"**

Removing "$@" fixes it. Thank you for the program!

---

