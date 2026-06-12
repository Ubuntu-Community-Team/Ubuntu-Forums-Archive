---
title: "Help installing thunderbird from source?"
date: 2011-02-25
forum: General Help
---

### Post by brallan on 2011-02-25
Since I cannot find a deb of thunderbird 3.3, I would like to find  another way to install 3.3 on maverick. I have no experience installing  from source, so I may need to be coached through it step by step, but I  am eager to learn and VERY motivated

Why? I am trying to switch  from gmail webmail to thunderbird, because of enigmail and privacy.  However, I have been spoiled by gmail's elegance, and in order to get  the conversation view add-on, so thunderbird still looks like gmail, the  add-on requires the 3.3 version of thunderbird. The latest stable  version which is in the repos (maverick) is older (3.1).

I have already have done the following:

```
sudo apt-get install build-essential
```then i downloaded [the files]("http://download.mozilla.org/?product=thunderbird-3.3a2&os=linux&lang=en-US") and extracted to my home directory.

now, according to the [ubuntugeek]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html"), I should execute the following commands:

```
./configure make
 sudo make install
 clean install

```but I have a few doubts:

1) Should I first uninstall thunderbird 3.1? and enigmail?
2) Where do I install it, so it can still find my mails and work as now?
3) If it doesn't work out, can I go back, and if so, how? Once installed, will it be uninstallable from apt or synaptic?
4) Will Ubuntu continue to upgrade my thunderbird once a newer version is available at some time in the future?

---

### Post by oldsoundguy on 2011-02-25
Why? Thunderbird is in the repositories and under synaptic.  It is also in the Software Center.

---

### Post by DougieFresh4U on 2011-02-25
Not sure how I did it but can be done, sorry:)
Extracted it to Downloads I think, and 'viewed files' and that's where I got lost as I was clicking things and finally some thing gave me a c'choice' to 'Display' or 'Run'

---

### Post by brallan on 2011-02-26
> **oldsoundguy said:**
> Why? Thunderbird is in the repositories and under synaptic.  It is also in the Software Center.

Yes, thunderbird 3.1 IS indeed in the repositories. But I am trying to install a plugin which is only available for the alpha 3.3 version of thunderbird.

---

### Post by brallan on 2011-02-26
> **DougieFresh4U said:**
> Not sure how I did it but can be done, sorry:)
Extracted it to Downloads I think, and 'viewed files' and that's where I got lost as I was clicking things and finally some thing gave me a c'choice' to 'Display' or 'Run'

thanks for trying, DougieFresh!

I think that compiling from source must be done from the command line, probably using the commands above. I am looking for someone with compiling experience to advise me through the process. 

Before I get started I want to know: 

1) If I should uninstall the current stable version (3.1) FIRST
2) If it will import my mails or DELETE THEM
3) how to install it in the same place ubuntu installs it so it still works the same

etc.

thanks!

---

### Post by jocko on 2011-02-26
> **brallan said:**
> I think that compiling from source must be done from the command line, probably using the commands above. I am looking for someone with compiling experience to advise me through the process. 

Before I get started I want to know: 

1) If I should uninstall the current stable version (3.1) FIRST
2) If it will import my mails or DELETE THEM
3) how to install it in the same place ubuntu installs it so it still works the same

etc.

thanks!
The file you downloaded does not contain any source code, so there is nothing to compile. You don't even have to install it. Just extract it in your home folder (or anywhere else you want it) and run it by double-clicking the file "thunderbird" in the extracted folder (or make a starter that points to it).

1. I don't think you will need to uninstall your current (stable) version of thunderbird, but I guess it is not impossible that some config files or plugins from the alpha version may conflict with the stable version, so make a backup of your ~/.thunderbird folder (hidden in your home directory) before you run the alpha version.

2. All config files are kept in your ~/.thunderbird directory, so if you have already imported all your mails to the stable version of thunderbird, they should automatically be available in the alpha version without the need to import anything (but make a backup of your ~/.thunderbird folder just in case. 3.3 is still an alpha version, which means it is not considered stable).

3. That's a bit complicated. You would probably have to manually move every file to their new locations and probably edit some of the run scripts and configuration files to reflect the new locations. Just keep everything in the extracted folder (you can keep the folder anywhere you want to) and make a custom starter and/or a symlink in a folder in your $PATH (e.g. /usr/local/bin).

---

### Post by brallan on 2011-02-26
I saw that even the [verson in natty]("http://packages.ubuntu.com/natty/mail/") will be thunderbird (3.1.8+build3+nobinonly-0ubuntu1), which is a bummer. the windows folks and mac folks already have an installer, but I am going to ask for help putting together a deb file, since i will surely not be the only one wanting this add-on.

---

### Post by brallan on 2011-02-26
Great Jocko! that should do it, I will try all of that, sounds like a great solution.

---

### Post by brallan on 2011-02-27
oops, did indeed get it working, except enigmail does not work within the conversation view! For encrypted messages, I have to change back to the classic reader. oh well, its inconvenient, but quite manageable.

---

### Post by mekmar on 2011-02-28
It would be great, if Mozllla Team guys made ppa with just testing Thunderbird. Right now even in daily repo there's only 3.1 pre-release versions.

---

