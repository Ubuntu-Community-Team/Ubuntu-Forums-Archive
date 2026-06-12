---
title: "ubuntu 10.04 tor and vidalia not working"
date: 2010-06-02
forum: General Help
---

### Post by zerobinary on 2010-06-02
Can't configure out how to configure it Need help please
> Jun 01 23:18:15.605 [Notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jun 01 23:18:15.605 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jun 01 23:18:15.606 [Notice] Opening Socks listener on 127.0.0.1:9050
Jun 01 23:18:15.606 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jun 01 23:18:15.606 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 01 23:18:15.606 [Error] Reading config failed--see warnings above.
Jun 01 23:18:21.714 [Notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jun 01 23:18:21.715 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jun 01 23:18:21.715 [Notice] Opening Socks listener on 127.0.0.1:9050
Jun 01 23:18:21.715 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jun 01 23:18:21.716 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 01 23:18:21.716 [Error] Reading config failed--see warnings above.
Jun 01 23:18:25.411 [Notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jun 01 23:18:25.411 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jun 01 23:18:25.412 [Notice] Opening Socks listener on 127.0.0.1:9050
Jun 01 23:18:25.412 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jun 01 23:18:25.412 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 01 23:18:25.412 [Error] Reading config failed--see warnings above.

---

### Post by zerobinary on 2010-06-02
Please help

---

### Post by closetpokey on 2010-06-21
EDIT: Here is the sollution [http://ubuntuforums.org/showpost.php?p=9226418&postcount=3](http://ubuntuforums.org/showpost.php?p=9226418&postcount=3)

The problem is that the Tor service is being called to run *before* Vidalia calls it to run, that's generating the error you see. I had this problem myself, and someone pointed me to (i think it was a command to run in terminal) to disable Tor from startup... and let Vidalia load Tor. Then you had to add Vidalia to your startup list.

So basically Tor is not allowed to start itself first, you need to let Vidalia load Tor instead. I'm sorry I don't remember how to do this... I'm actually looking for the sollution myself as I found it once before but did not bookmark the page. If you can build upon what I've explained so far and find a way to fix it please post it here! Thanks, hope I helped a little...

oRioN

---

### Post by Zeblue on 2011-01-04
I know this thread is old, but thought I'd share how I just solved this same problem.

[LIST=7]
[*]Go to System -> Administration -> Synaptic Package Manager
[*]In the quick search type "Vidalia"
[*]Right click on the listed Vidalia package and click "Mark for Complete Removal"
[*]Click the big green "Apply" check mark and click apply in the next window that pops up. Next, click the close button and exit Synaptic Package Manager.
[*]Go to Applications -> Accessories -> Terminal
[*]Enter into the terminal "sudo apt-get install vidalia"
[*]Eventually, the terminal window will turn blue and give you three options to choose from. Select the third option (you want Vidalia to open Tor every time).[/LIST]

Now, you're good to go.

---

### Post by skyssa on 2011-03-07
Thank you!!!

---

### Post by CyralSnear on 2011-04-10
Hi yall.

 after 

[LIST=1]
[*]Go to System -> Administration -> Synaptic Package Manager
[*]In the quick search type "Vidalia"
[*]Right click on the listed Vidalia package and click "Mark for Complete Removal"
[*]Click the big green "Apply" check mark and click apply in the next  window that pops up. Next, click the close button and exit Synaptic  Package Manager.
[*]Go to Applications -> Accessories -> Terminal
[*]Enter into the terminal "sudo apt-get install vidalia"
[*]Eventually, the terminal window will turn blue and give you three  options to choose from. Select the third option (you want Vidalia to  open Tor every time).
[/LIST]

i had this message in terminal 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any input would be much appreciated

---

### Post by kn0w-b1nary on 2012-01-06
> **CyralSnear said:**
> Hi yall.

 after 

[LIST=1]
[*]Go to System -> Administration -> Synaptic Package Manager
[*]In the quick search type "Vidalia"
[*]Right click on the listed Vidalia package and click "Mark for Complete Removal"
[*]Click the big green "Apply" check mark and click apply in the next  window that pops up. Next, click the close button and exit Synaptic  Package Manager.
[*]Go to Applications -> Accessories -> Terminal
[*]Enter into the terminal "sudo apt-get install vidalia"
[*]Eventually, the terminal window will turn blue and give you three  options to choose from. Select the third option (you want Vidalia to  open Tor every time).
[/LIST]

i had this message in terminal 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any input would be much appreciated

I know this is old, but anyways...

You probably did NOT close Synaptic, you have to in order to use apt-get from terminal. ;)

---

### Post by nilsja on 2012-11-27
> **Zeblue said:**
> I know this thread is old, but thought I'd share how I just solved this same problem.

[LIST=7]
[*]Go to System -> Administration -> Synaptic Package Manager
[*]In the quick search type "Vidalia"
[*]Right click on the listed Vidalia package and click "Mark for Complete Removal"
[*]Click the big green "Apply" check mark and click apply in the next window that pops up. Next, click the close button and exit Synaptic Package Manager.
[*]Go to Applications -> Accessories -> Terminal
[*]Enter into the terminal "sudo apt-get install vidalia"
[*]Eventually, the terminal window will turn blue and give you three options to choose from. Select the third option (you want Vidalia to open Tor every time).[/LIST]

Now, you're good to go.

If you use the terminal anyway you can shorten the steps:
[LIST=1]
[*]Go to Applications -> Accessories -> Terminal
[*]Enter into the terminal "sudo apt-get remove --purge vidalia tor"
[*]Enter into the terminal "sudo apt-get install vidalia"
[*]Eventually, the terminal window will turn blue and give you three options to choose from. Select the third option (you want Vidalia to open Tor every time).[/LIST]

---

