---
title: "ERROR: Cannot open OSS audio device /dev/dsp"
date: 2011-10-12
forum: General Help
---

### Post by 0603008w on 2011-10-12
I am working on a program called HTK which is a speech recognition software. It can run live inputs i.e. a person speaks and the spoken word is transcribed onto the terminal. The error i get is:
Cannot open OSS audio device /dev/dsp

I have installed ALSA sound mixer for GNOME, and i still get the error. Please advice on what sound drivers i need to install.

Thanks

---

### Post by wolfen69 on 2011-10-12
Try installing oss-compat
```
sudo apt-get install oss-compat
```
it adds a compatibility layer between alsa and oss.

---

### Post by 0603008w on 2011-10-12
Hi wolfen69

Thanks for the quick response

It is the first time im using this forum, so i sent two threads by mistake. I tried your suggestion and now im getting warning:
WARNING [-6006] ReadAudio: Failed to read all 0 examples from OSS audio in HVite.

This indicates that there it is still not reading from OSS. The HVite command that is run using HTK is as follow: 
HVite -H hmm15/macros -H hmm15/hmmdefs -C config2 -w wdnet -p 0.0 -s 5.0 dict tiedlist

---

### Post by dabraude on 2011-10-14
After speaking to them I figured out this way to solve the problem

First install 
alsa-oss

and
 
ia32-alsa-oss   
[INDENT]from: [http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb")[/INDENT]


(I have also installed oss-compat but I don't think it will have an effect on this)



Then run it with 

LD_PRELOAD=/usr/lib32/libaoss.so aoss HVite -H hmm15/macros -H hmm15/hmmdefs -C config2 -w wdnet -p 0.0 -s 5.0 dict tiedlist

It does run but gives the following errors:
ERROR: ld.so: object '/usr/lib32/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

Any ideas how to get rid of that?

---

### Post by dabraude on 2011-10-14
I have fixed the problem

create a copy of aoss in your /usr/bin/ directory (I called it aoss32)

edit aoss32 and change the line 

LD_PRELOAD=${exec_prefix}/**lib**/libaoss.so${LD_PRELOAD:+:$LD_PRELOAD} exec "$@"

to 

LD_PRELOAD=${exec_prefix}/**lib32**/libaoss.so${LD_PRELOAD:+:$LD_PRELOAD} exec "$@"



then run HVite with
aoss32 HVite -H hmm15/macros -H hmm15/hmmdefs -C config2 -w wdnet -p 0.0 -s 5.0 dict tiedlist

---

### Post by noegroz1987 on 2012-02-14
> **dabraude said:**
> I have fixed the problem

create a copy of aoss in your /usr/bin/ directory (I called it aoss32)

edit aoss32 and change the line 

LD_PRELOAD=${exec_prefix}/**lib**/libaoss.so${LD_PRELOAD:+:$LD_PRELOAD} exec "$@"

to 

LD_PRELOAD=${exec_prefix}/**lib32**/libaoss.so${LD_PRELOAD:+:$LD_PRELOAD} exec "$@"



then run HVite with
aoss32 HVite -H hmm15/macros -H hmm15/hmmdefs -C config2 -w wdnet -p 0.0 -s 5.0 dict tiedlist

Hi,
I followed your step.
But, I got this error message:

HVite: error while loading shared libraries: libalsatoss.so.0: wrong ELF class: ELFCLASS64

any idea?

---

### Post by HiImTye on 2012-02-14
run your program with 'padsp' before it, for example:
```
padsp avidemux
```would start avidemux (video editor) with OSS compatability.

padsp is an OSS wrapper for PulseAudio. you might experience some audio problems but for now, this should allow you to launch the program and if you do have issues you can come back and we can figure them out

---

### Post by dabraude on 2012-02-14
Audio issues are a big problem as this is speech recognition software ;)

try this:
[http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-64bit-environments/373367-playing-wmv-files-10-1-x86_64-a.html](http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-64bit-environments/373367-playing-wmv-files-10-1-x86_64-a.html)

also did you install oss-compat?
I wasn;t sure if it had an effect but it might

---

