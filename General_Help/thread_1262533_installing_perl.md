---
title: "installing perl"
date: 2009-09-10
forum: General Help
---

### Post by oospill on 2009-09-10
hello.  I'm trying to get my ipod shuffle to work with linux.  I found a project called GNUpod ([http://www.gnu.org/software/gnupod/](http://www.gnu.org/software/gnupod/)) which uses perl, and a nice fellar that made some perl scripts to make the job of GNUpod a little easier ([http://www.cs.utexas.edu/~walter/geek/ipodshuffle-linux.html](http://www.cs.utexas.edu/~walter/geek/ipodshuffle-linux.html)).

I should be able to figure all that out, but the docs tell me I have to have perl installed.  when searching 'perl' in synaptic, I found hundreds of entries.  

help me install perl!! ack!!

thanks, 
oospill

---

### Post by Perfect Storm on 2009-09-10
gnupod is in the repository.
Either find gnupod-tools in synaptic package Manager or;

```
sudo apt-get install gnupod-tools
```


Note, that gnupod is a commandline tool.

---

### Post by bhaverkamp on 2009-09-10
Perl is installed by default.

'perl -v' should confirm this by display the installed version info

---

### Post by oospill on 2009-09-10
I'm cool with gnupod being command line.

alright.. I'm reading the gnupod docs right now.. but this is a great time for me to ask a few questions.  after installing gnupod, what directory do I need to be in to run it?  how do I tell what dir to be in for new programs that I download?

and how did you find that it was available in the repositories?

and just for fun.. is there an analouge to the old PATH statement I used in the autoexec.bat in dos? (.bashrc?)

thanks,
oospill

so far, all my beans are questions. =/ you peeps rock!

---

### Post by niteshifter on 2009-09-10
> **oospill said:**
> I'm cool with gnupod being command line.

alright.. I'm reading the gnupod docs right now.. but this is a great time for me to ask a few questions.  after installing gnupod, what directory do I need to be in to run it?  how do I tell what dir to be in for new programs that I download?

If gnupod needs to be run from a specific directory, it's docs will tell that. But generally "stuff" you download from the repos goes into /bin or /usr/bin and so forth automagically. These dirs are already on your path.

> 
and how did you find that it was available in the repositories?


I've long suspected Artificial Intelligence is exactly that and had such info burned into his/her/it's basic rom set by the Master Programmer.

Or it could be AI used the Search function in Synaptic Package Manager ;)

> 
and just for fun.. is there an analouge to the old PATH statement I used in the autoexec.bat in dos? (.bashrc?)

Yes. Not coincidentally it's called PATH (it's from Unix MS 'borrowed' this). Try this in Terminal:
```
echo $PATH
```
That will show your current executable search path. As to manipulating it ... I wouldn't - until I'd learned a bit more about shells & such. Generally it's left alone. If you're wondering how any scripts or programs you write can be picked up: Easy is. Create a directory bin in your home folder:
```
cd ~         # let's make sure we are in /home/<us>
mkdir bin    # make the directory

```
On next reboot (or just logout and back in) that bin directory will be added to your path automatically.

---

### Post by Perfect Storm on 2009-09-10
> I've long suspected Artificial Intelligence is exactly that and had such info burned into his/her/it's basic rom set by the Master Programmer.

Or it could be AI used the Search function in Synaptic Package Manager

I'm only off-line when the Ubuntu Counsel put me on maintenance. :popcorn:

---

