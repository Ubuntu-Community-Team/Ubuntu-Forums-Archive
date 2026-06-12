---
title: "Help, I can't download"
date: 2012-01-29
forum: General Help
---

### Post by Vexiant on 2012-01-29
Hello,
when I try to download the Android SDK and such for Eclipse, it won't let me, it gives me an error message. It's the same if I try downloading from the Ubuntu Software Center. This has been happening ever since I installed Tor and Vidalia. I know it's Vidalia, though. I can download on Chrome and via terminal.

Thanks in advance.

I did this tutorial: [http://www.youtube.com/watch?v=azqjTrUraRU](http://www.youtube.com/watch?v=azqjTrUraRU)
Typed:
"echo "deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) experimental-lucid main" | sudo tee -a /etc/apt/sources.list

apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 886DDD89"
into terminal, also. (As it said to)

---

### Post by winh8r on 2012-01-29
Hi, sorry if i cannot "fix" your issue instantly.The first question I have to ask is "Do you really need to be using Tor/Vidalia?" Tor is an ultra anonynimty network which is very complex in the way it operates and WILL slow your browsing down by at least 50% possibly more.
Unless you are in a situation where anonynimity is 100% necessary due to political/security/censorship reasons, I would suggest removing Tor and Vidalia from your system.
Secondly, when you see a tutorial on a video sharing site it is always advisable to check up on exactly what commands you see being used and find out what they do , BEFORE you enter them into your terminal. The security of any system can be compromised by entering one or two commands at the terminal allowing unauthorised access to your system and/or loss of data.

One more point, when typing in commands to the terminal which are qouted in another place/page it is usual to type in the command WITHOUT the quote (" ") marks around the text. Commands that are written down in a list format should be entered one at a time.
A command that has more than one part will generally use the | (pipe) symbol or contain the && symbols between the parts of the command.

If you require intermittent anonymity during your surfing then I would suggest searching for a list of public proxy servers and bookmarking one of them for occassional use, however be aware that any proxy you use is only as secure as the people or person providing it, your data may still be visible to the proxy operator.

The best way to keep your system in good order is to install only those applications which you actually need, if you find that something is not doing what you wanted then please remember to remove it from your system when you no longer use it.
You can open the synaptic package manager and click on the "installed" tab to see what is installed on your system. When removing software remember to read the info box that pops up when you click "apply" in order to make sure that removing one piece of software and its dependencies will not remove a dependency for something else which is still being used.

I hope this is of some small amount of use to you.

Good luck with your developing too!

---

### Post by fhgaminguk on 2012-01-29
> **Vexiant said:**
> Hello,
when I try to download the Android SDK and such for Eclipse, it won't let me, it gives me an error message. It's the same if I try downloading from the Ubuntu Software Center. This has been happening ever since I installed Tor and Vidalia. I know it's Vidalia, though. I can download on Chrome and via terminal.

Thanks in advance.

I did this tutorial: [http://www.youtube.com/watch?v=azqjTrUraRU](http://www.youtube.com/watch?v=azqjTrUraRU)
Typed:
"echo "deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) experimental-lucid main" | sudo tee -a /etc/apt/sources.list

apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 886DDD89"
into terminal, also. (As it said to)

I suggest you remove Tor and Vidalia then. Type into terminal: sudo apt-get remove tor 
Then do the same for vidalia (I believe that's the right command line anyways). If you are doing it for anonymous reasons, then I suggest you setup a VPN through the 'network' setup. Or dual boot with windows and download a VPN through that, and use windows as and when you want to remain anonymous.

---

### Post by TheFu on 2012-01-29
> **fhgaminguk said:**
> Or dual boot with windows and download a VPN through that, and use windows as and when you want to remain anonymous.

This is less than ideal advice.  Using MS-Windows on the internet is dangerous. Another option needs to be provided.

To the OP, when you installed TOR, you may have set it up for all users or just a single user.  I'd recommend you check your network configuration:

$ ifconfig
$ route print
$ sudo iptables -L

Save the outputs from those commands with and without tor installed. That should help you determine what the issue is.

For some reason, I thought tor worked through a proxy service, so if you check the proxy settings in your browser, you may be able to bypass tor there which will be much easier. I'd start there.

You'll need to understand networking a little better to figure out exactly what's going on. Sorry, but I don't use tor, so I can't provide any short-cuts to a solution.  Removing tor may be an option to get you started.  Then you can work out a way to enable it and disable it as desired.  

You are running Linux and can script almost anything pretty easily after all.

---

### Post by Vexiant on 2012-01-29
Well, I do need to stay anonymous once I move. It's too long of a story to elaborate on. So I really need to find out how to download from the Ubuntu Software Center while having Tor and Vidalia installed; it's a must!

Edit: Once I download what I need of the Software Center, I'll reinstall Vidalia and Tor because I think what I did wrong was allowing Chromium to make "System Wide Changes," rather than just for Chrome, etc. :P

Edit2: Works!

---

