---
title: "Using 10.10, Google Won't Let Me Access Blogger -- Malware?"
date: 2011-10-27
forum: General Help
---

### Post by mohab on 2011-10-27
'Our systems have detected unusual traffic from your computer network.' 

I get this message when I try to access Blogger along with being blocked from any blogs that use Blogger. The first time I saw it I had Tumblr open in another window, which made me wonder if that open window with a huge social network running on it caused the problem. 

After a couple of days I was no longer blocked from Blogger and didn't get the above message, but today I got the message again I tried to read any of Blogger's blogs.

Is this malware? 

I'm not too tech savvy and I've been trying to download spy programs to see if any malware is on my computer or if its a Google quirk (some people have thought it's a Google problem); so far I've been unable to get any to work, clamav for one, and don't know if I was trying the right solutions. I ran Avast and it found no viruses, but I don't know if Avast checks any, or all kinds, of malware. 

I'm also due for an update on my Ubuntu version so I was wondering if a fresh install would rid a computer of malware, if it were the problem, and I wouldn't mind going this route.

Can anyone clarify if this is malware or a Google quirk and what my best options are if malware is the problem.

Update: I just tried accessing blogger again and was able to this time. This leads me to believe Google is the problem and not any malware. I could be wrong.

---

### Post by mohab on 2011-10-29
I am getting blocked again at Blogger with this message from Goggle:

> Our systems have detected unusual traffic from your computer network. Please try your request again later. Why did this happen?

This page appears when Google automatically detects requests coming from your computer network which appear to be in violation of the Terms of Service. The block will expire shortly after those requests stop.

This traffic may have been sent by malicious software, a browser plug-in, or a script that sends automated requests. If you share your network connection, ask your administrator for help — a different computer using the same IP address may be responsible. Learn more

Sometimes you may see this page if you are using advanced terms that robots are known to use, or sending requests very quickly. 



Sometimes I don't get blocked at other times I do. As you can see the message suggests a script may be in my computer sending automatic requests.

Can anyone tell me if this is malware, or if that can happen using Ubuntu? If it appears to be malware, what can I do to fix it and prevent it in the future? 

I'm thinking a brand new install might correct the problem, am I right?

Thanks in advance for any help with this.

---

### Post by ppv on 2011-10-29
Can you try it using a different browser. If its a browser plugin then you shouldn't see the problem with a different browser.
 
Or you may even try the no add-ons options of the browser you are using. Most new popular browsers have this option.

---

### Post by mohab on 2011-10-29
Thanks. I tried Chromium and removed my add ons from Firefox, but the problem persists. I'm thinking maybe a fresh install might be my best option, perhaps adding a firewall for future protection.

---

### Post by jon zendatta on 2011-10-29
If you suspect you're malware infected, check this sticky [http://ubuntuforums.org/showthread.php?t=1477662]("http://ubuntuforums.org/showthread.php?t=1477662"):KS

---

### Post by mohab on 2011-10-29
Thanks. I like these quotes:

"Many Linux users may feel these tools are of limited utility ...." 

"Although every OS has potential security holes, many users find Ubuntu is "secure enough" such that additional measures are not warranted."

I didn't think malware could attack Linux, but this persistent problem has me a little concerned. It might be a Google glitch, but I've no way to be sure. Thus, I'm thinking maybe a new install would be my best bet. Would 11.04 be any more secure than 10.04?

---

### Post by gandaran on 2011-10-29
try cleaning the browsers cookies and cache before accessing blogger, should fix the problem unless your ubuntu computer is not the only one working on the network, certainly it's not a malware problem.

---

### Post by mohab on 2011-10-29
Thanks. I will give that a try. My computer is the only one on the network.

---

### Post by mohab on 2011-10-29
> try cleaning the browsers cookies and cache before accessing blogger, should fix the problem.

That fixed the problem. Thanks again.

---

### Post by oldtimer7777 on 2011-10-29
> **mohab said:**
> That fixed the problem. Thanks again.

I use Bleachbit religiously.

sudo apt-get install bleachbit
sudo bleachbit

No problems. Just fast browsing all the time. If I ever have a concern I use bleachbit and I am back at full speed in my browser again.  Works like a charm.:D

---

### Post by mohab on 2011-10-29
Thanks.  Sounds outstanding. I just installed it.

---

