---
title: "Repositories"
date: 2012-03-16
forum: General Help
---

### Post by Lechatelier on 2012-03-16
This is probably a silly question but really puzzles me: 
I Have Ubuntu 9.04  9.10 and 12.04 installed. I need to keep both old ones for reasons of hardware compatibility. When I tried to install some programs I receive responses like these ones:

W: Failed to fetch [http://ftp.ccc.uba.ar/pub/linux/ubuntu/pool/main/l/lm-sensors-3/libsensors4_3.0.2-2ubuntu4_i386.deb](http://ftp.ccc.uba.ar/pub/linux/ubuntu/pool/main/l/lm-sensors-3/libsensors4_3.0.2-2ubuntu4_i386.deb)
  404  Not Found

W: Failed to fetch [http://ftp.ccc.uba.ar/pub/linux/ubuntu/pool/main/l/lm-sensors-3/lm-sensors_3.0.2-2ubuntu4_i386.deb](http://ftp.ccc.uba.ar/pub/linux/ubuntu/pool/main/l/lm-sensors-3/lm-sensors_3.0.2-2ubuntu4_i386.deb)
  404  Not Found
I tried changing repositories without success. 
Is this normal?
Will many or all old programs disappear in time?
Regards

---

### Post by imachavel on 2012-03-16
what do you mean when you say you tried to change repositories?

---

### Post by raja.genupula on 2012-03-16
your 9.04 and 9.10 both EOL actually . so you're unable to install any applications from them . 

to install applications from them you need to some modification on source files . i mean look at this 
[http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)

---

### Post by pinguinhood on 2012-03-16
Do you have 3 partition or do you have installed package of these 3 OS only changing repositories???:confused:

---

### Post by imachavel on 2012-03-16
wtf, I would imagine either 3 partitions or 3 separate drives. He said he has each previous version of the main OS installed.

raja.genupula

you are saying from this:

[http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)

Access repositories on EOL (End of Life) Ubuntu Releases
	 
A normal Ubuntu release is supported for 18 months on both Server and Desktop editions where as an LTS (Long Term Support) release is supported for 3 years on the Desktop whereas 5 years on Server edition. For a list of Ubuntu releases, see here.

that those previous Ubuntu versions are only supported for 18 months as opposed to 3 years? Isn't Ubuntu the most supported version of the linux kernel right now? Why would the support be so low. Even windows xp in some cases is still updated and what not and supported, and that will probably phase out when windows 8 comes out, but lol dude wtf why so short term support for linux distro version?

---

### Post by snowpine on 2012-03-16
> **imachavel said:**
> that those previous Ubuntu versions are only supported for 18 months as opposed to 3 years? Isn't Ubuntu the most supported version of the linux kernel right now? Why would the support be so low. Even windows xp in some cases is still updated and what not and supported, and that will probably phase out when windows 8 comes out, but lol dude wtf why so short term support for linux distro version?

Most Ubuntu users enjoy keeping up with the latest software, therefore 6-month releases with 18-months support by default.

For users who prefer stability, there is the LTS release cycle with 5 years of support.

Win-win situation; users can choose whichever works best for them.

---

### Post by raja.genupula on 2012-03-16
> **imachavel said:**
> wtf, I would imagine either 3 partitions or 3 separate drives. He said he has each previous version of the main OS installed.

raja.genupula

you are saying from this:

[http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)

Access repositories on EOL (End of Life) Ubuntu Releases
	 
A normal Ubuntu release is supported for 18 months on both Server and Desktop editions where as an LTS (Long Term Support) release is supported for 3 years on the Desktop whereas 5 years on Server edition. For a list of Ubuntu releases, see here.

that those previous Ubuntu versions are only supported for 18 months as opposed to 3 years? Isn't Ubuntu the most supported version of the linux kernel right now? Why would the support be so low. Even windows xp in some cases is still updated and what not and supported, and that will probably phase out when windows 8 comes out, but lol dude wtf why so short term support for linux distro version?

cool my friend .
first read this 
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
LTS extended for 5 years for both desktop and server .

---

### Post by Lechatelier on 2012-03-16
> **raja.genupula said:**
> your 9.04 and 9.10 both EOL actually . so you're unable to install any applications from them . 

to install applications from them you need to some modification on source files . i mean look at this 
[http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)
The reference recommends replacing archive.ubuntu.com with old-releases.ubuntu.com in /etc/apt/sources.list. I Could not find archive.ubuntu.com in that file.

I found another reference:
[http://thinkbeforetype.com/2010/12/12/accessing-ubuntus-end-of-life-repositories/](http://thinkbeforetype.com/2010/12/12/accessing-ubuntus-end-of-life-repositories/)
which recommended adding new lines in the same file. When doing apt-get update it produced lots of errors similar to those I mentioned in my original. When I tried to install the programs I wanted I encountered exactly the same error.

Taking a look to the error themselves I noticed the appear to point
to files in a server in Argentina  ¿Is it possible those files are supposed to be only in those servers? ¿Is it possible finding them somewhere else?
By the way I have two computers with two disks each one is running 9.04 because 9.10 does not recognize the sound system. The other one has 9.10 and 10.04 in different disks. I am now using 9.10 because 10.04 does not go along with the new network card.
Regars.

---

### Post by raja.genupula on 2012-03-16
give a try by holding the server as Main-server .

---

### Post by Lechatelier on 2012-03-17
I have solved my problem by googling the name of the programs.

This way I  found: 

[https://launchpad.net/ubuntu/+source/lm-sensors-3/1:3.0.2-2ubuntu4/+build/893909](https://launchpad.net/ubuntu/+source/lm-sensors-3/1:3.0.2-2ubuntu4/+build/893909).

There were both .deb packages. Just downloaded and installed. 

Maybe it workes in a few cases so a more general solution would be useful specially now that desk 10.04 is reaching end of life.

---

### Post by oldos2er on 2012-03-17
10.04 desktop version won't reach EOL until April 2013.

---

