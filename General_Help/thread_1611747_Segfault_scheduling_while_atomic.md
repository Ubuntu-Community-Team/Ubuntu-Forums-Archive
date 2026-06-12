---
title: "Segfault scheduling while atomic"
date: 2010-11-02
forum: General Help
---

### Post by jamillikan on 2010-11-02
On 10.04 LTS I still experience a sefault in dosemu with one program that is critical to our business.  I have been unable to find a solution other than using kernel 2.6.27 where the program works perfectly.

If you are a kernel developer (or know someone who is) could someone PLEASE address this issue and resolve it so our company may move forward without this regression?

Any help is appreciated.  FWIW, I've reported it on Launchpad to no avail.  

Thank you.  

At wit's end.

---

### Post by Brandon Williams on 2010-11-02
We will have a hard time offering suggestions if you don't provide any information about what's happening. For example, is your problem related to [this bug](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/217710) and [this bug](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/216398)? Both of them are caused by the same issue, they describe a workaround, and there are bug reports for other distros that discuss the same bug and the same workaround.

On another note, if you're not getting attention via launchpad, then you should probably try escalating to the upstream developers. Coming to the forums is fine if what you're looking for is a workaround or bug confirmation. If you're looking for a fix, you probably won't get it here.

---

### Post by jamillikan on 2010-11-02
Thank you for your suggestion.  How do I contact the upstream developers?

---

### Post by Brandon Williams on 2010-11-02
The developer's website is [http://www.dosemu.org/](http://www.dosemu.org/) and they have both a bug tracking system and a support request tracking system there. That said, dosemu does not appear to be in active development. There has not been a new version for 3 years most bugs/support request that have been filed over the past few years have not gotten any attention. This may be why you haven't gotten any help via launchpad.

Unfortunately, it may be that your only option is to continue running the older kernel, since dosemu is not supported by ubuntu (it's in the multiverse repo) and doesn't appear to get much (if any) developer attention.

---

### Post by jamillikan on 2010-11-25
Thanks for the info Brandon.  In the meantime, I figured out a solution to the problem.  Everything works perfectly EXCEPT Dictionary Editing on 10.04.1 LTS, so I just installed Intrepid in a VMware Machine on 10.04 LTS, shared the folder containing the dictionaries in 10.04.1 LTS with the Virtual Machine, problem solved as far as editing the personal dictionaries.

I just needed to think about a logical solution.  Works perfectly!  Problem solved.  Continuing to move forward.

---

