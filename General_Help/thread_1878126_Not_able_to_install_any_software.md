---
title: "Not able to install any software"
date: 2011-11-09
forum: General Help
---

### Post by vishal060 on 2011-11-09
I am trying to use Ubuntu software center to install applications in my laptop.
But every time i try doing so i get a message ' Check your Internet connection'
I am using an internet connection with proxy server and i have already entered the same in system proxy settings....So please guide me

---

### Post by ballantony on 2011-11-09
Can you see the internet via your web browser?

---

### Post by vishal060 on 2011-11-09
@ballantony:- 
yes i can ..
i m accessing internet right now through same laptop

---

### Post by ballantony on 2011-11-09
I f I remember correctly, 

(sudo) edit /etc/apt/apt.conf  
and add the line

Acquire::http::   Proxy::"http://your.proxy";

Hope that helps!

---

### Post by vishal060 on 2011-11-09
One more thing i m able to install same using terminal....
So is there any setting to be changed while  using Ubuntu software center..
please clarify

---

### Post by ballantony on 2011-11-09
I'm not working through a proxy at the moment so I can't check...

---

### Post by Seb71 on 2011-11-09
Does it work with a direct connection to the Internet (without proxy server)?

---

### Post by vishal060 on 2011-11-09
ballantony:
But that part is already updated with my proxy setting..

---

### Post by vishal060 on 2011-11-09
@ Seb 71
I dont have a direct internet connection..
So i cant clarify this thing

---

### Post by ballantony on 2011-11-09
Is it?  Sorry, I seem to remember having to do it that way when having the same problem at work.  I'll take a look next time I'm there if no one solves your problem in the mean time.

---

### Post by vishal060 on 2011-11-09
@ballantony
Thanks
I will look forward to see ur reply

---

### Post by ballantony on 2011-11-09
Just a thought, you're not trying to authenticate to a windows server are you?

---

### Post by vishal060 on 2011-11-09
I dont ha[I]ve exact idea.
But i m  using my companies internet connection.
and all the support to them is pro[/I]*vided by IBM*

---

### Post by ballantony on 2011-11-09
Ah.  You might not be authenticating through the proxy if they're using microsoft proxy servers.  I had this problem and I had to use ntlmaps to get through...

[http://www.linuxquestions.org/linux/answers/Networking/HOWTO_Install_and_Configure_NTLMaps_for_use_with_an_ISA_Proxy](http://www.linuxquestions.org/linux/answers/Networking/HOWTO_Install_and_Configure_NTLMaps_for_use_with_an_ISA_Proxy)

---

