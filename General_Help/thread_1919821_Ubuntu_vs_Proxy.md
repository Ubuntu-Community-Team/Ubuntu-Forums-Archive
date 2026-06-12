---
title: "Ubuntu vs Proxy"
date: 2012-02-03
forum: General Help
---

### Post by afz12 on 2012-02-03
I have problems updating Ubuntu through a proxy server. This is purely an Ubuntu issue and perfectly legal as Windows has no problems in any access area. Also, Synaptic works fine, (as do all web browsers etc) but all terminal commands fail. Also, the "software center" consistently fails. Interestingly the proxy access works fine from my home address but becomes problematic, only for Ubuntu, any distro, on location. Why is this? Is there a fix?

The IT people on location do not support Linux although a few faculties use Debian internally. I cannot affect policy with regard to what appears to be specific to Ubuntu, not the proxy server. Again, to reinforce, the transactions are pefectly acceptable to all IT policy, this is an issue specific to Ubuntu and then, only when accessed on location and then only for the update manager or software center but not for synaptic or web based software. Thanks for any suggestions in advance.

---

### Post by haqking on 2012-02-03
> **afz12 said:**
> I have problems updating Ubuntu through a proxy server. This is purely an Ubuntu issue and perfectly legal as Windows has no problems in any access area. Also, Synaptic works fine, (as do all web browsers etc) but all terminal commands fail. Also, the "software center" consistently fails. Interestingly the proxy access works fine from my home address but becomes problematic, only for Ubuntu, any distro, on location. Why is this? Is there a fix?

The IT people on location do not support Linux although a few faculties use Debian internally. I cannot affect policy with regard to what appears to be specific to Ubuntu, not the proxy server. Again, to reinforce, the transactions are pefectly acceptable to all IT policy, this is an issue specific to Ubuntu and then, only when accessed on location and then only for the update manager or software center but not for synaptic or web based software. Thanks for any suggestions in advance.

have you specified the proxy then ?

---

### Post by afz12 on 2012-02-03
It should be reasonable to expect this given that windows works and has proxy references and also that synaptic does the same.

---

### Post by cortman on 2012-02-03
By "terminal commands" I assume you're referring to apt-get, etc. If it's just an aptitude problem, you may need to add a line for the proxy in apt.conf. See this [how-to]("https://help.ubuntu.com/community/AptGet/Howto"), near the bottom.

---

### Post by afz12 on 2012-02-03
Thanks cortman - I'll give this a try :)

---

### Post by afz12 on 2012-02-03
Hi cortman - no joy

I tried this from the terminal to allow tempory proxy access
export http_proxy=http://yourproxyaddress:proxyport

with appropriate proxyaddress and port substituted - it needed a "sudo" i.e.

sudo export http_proxy=http://yourproxyaddress:proxyportwith password - this seemed OK so far

Then I tried to install octave3.2
sudo apt-get install octave3.2

It went through the 2 "permissions" but stopped at an error message "export: command not found!)

I then tried the "APT method" with

Acquire::http::Proxy "http://yourproxyaddress:proxyport";

I tried to add this line to the file at
/etc/apt/apt.conf

but the directory contained files. None allowed editing.

I tried this on Ubuntu 12.04 running as a virtual machine on a Win7 machine.

I then switched to synaptic and searched "octave3.2".
It downloaded easily and is now installed.

I admit I'm a bit flumixed at all this.
The terminal commands don't work on location.
Off location, the proxy is fine. Also the same issue occurs with the Software Center, again only on location.
Ubuntu 11.10 and Ubuntu 10.10 exhibit the same exact behavior, but I haven't tried these "fixes" on these VM's as yet.

Further, all web browsers work fine on location. Thunderbird also works fine on location. 
In all cases Win7 works fine on location.
On another notebook, XP works fine on location.

This behavior only seems to be expressed in Ubuntu.

At this stage, I guess an explanation would be as good as a fix :)

---

### Post by cortman on 2012-02-03
> **afz12 said:**
> 

I tried to add this line to the file at
/etc/apt/apt.conf

but the directory contained files. None allowed editing.


Did you try this with sudo?

```
gksu gedit /etc/apt/apt.conf
```

I use my laptop on my workplace wifi occasionally, and my apt.conf says

```
Acquire::http::proxy "http://192.168.0.1:8080/";
```

You could try adding that. Otherwise, I'm not sure why it's acting the way it is. Synaptic and the USC are just graphical front ends; their actual functionality is aptitude.

---

### Post by afz12 on 2012-02-03
Hi Cortman. Thanks for your time and suggestions. This on location software download behavior appears to be intractable. However, synaptic seems to work OK, for whatever reason! So far I've installed GNU Octave, qtoctave, VLC, python numpy, python spicy, python pylab, screenlets and cadsoft eagle through synaptic. Downloading files through Firefox also works fine. I think I'll forget about using the update manager, terminal or software center when on location. Maybe some future version of Ubuntu will have resolved this issue.

---

### Post by cortman on 2012-02-03
> **afz12 said:**
> Hi Cortman. Thanks for your time and suggestions. This on location software download behavior appears to be intractable. However, synaptic seems to work OK, for whatever reason! So far I've installed GNU Octave, qtoctave, VLC, python numpy, python spicy, python pylab, screenlets and cadsoft eagle through synaptic. Downloading files through Firefox also works fine. I think I'll forget about using the update manager, terminal or software center when on location. Maybe some future version of Ubuntu will have resolved this issue.

H'm. Very odd and puzzling. If you're satisfied though, all's well. Happy hacking!

---

