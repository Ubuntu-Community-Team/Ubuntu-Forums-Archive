---
title: "this ebay page makes my CPU heat up to 90c"
date: 2011-02-04
forum: General Help
---

### Post by sdowney717 on 2011-02-04
[http://cgi.ebay.com/25-lbs-BURNISHING-BALLS-3-16in-65-7300-001-Polishing-/400099089380?pt=LH_DefaultDomain_0&hash=item5d27c39be4#ht_724wt_913](http://cgi.ebay.com/25-lbs-BURNISHING-BALLS-3-16in-65-7300-001-Polishing-/400099089380?pt=LH_DefaultDomain_0&hash=item5d27c39be4#ht_724wt_913)

I tested this in Firefox and Opera and it cooks my CPU
In Chrome nothing, no overheating.

So what is going on?

---

### Post by sdowney717 on 2011-02-04
ok, chrome is doing it now. And has to do with when that image scrolls by at the page bottom.
Screen shot shows the temps.
You can see the monitor at the top moved way up and the temp is turning red on the CPU

IF I let it sit any longer, the temp climbs to 95c

---

### Post by Halkus on 2011-02-04
I had a check on Windows 7 x64 using Firefox and it ate a whole core. (AMD 1090T 6 cores). So whatever code is running that little nasty bit of graphics isn't good. That's why you're seeing the high load and as a result the high temperatures.

95 degrees is unsafe for CPUs in general. Something is wrong if it's going that high. What kind of computer are you running? Is it a desktop? A pentium D?

---

### Post by hansdown on 2011-02-04
It maxed out one of my cores, too.

---

### Post by viktorzk on 2011-02-04
> And has to do with when that image scrolls by at the page bottom. That is not an image, it looks like a Flash gallery. In Firefox I use the NoScript extension to block Flash when I don't need it.

---

### Post by psusi on 2011-02-04
You need to fix your heatsink/fan.  Maxing out just one out of six cores should not get you anywhere near 90 C.  It shouldn't get you above 60 C.  The only time you should see 80 or above is if you are hammering all cores at full tilt.

---

### Post by Halkus on 2011-02-04
Psusi, it's me with the 6 cores. I suspect the OP is on a single core, by the time CPUs got to multicore, even just 2, 95 degrees would have caused a throttling, or a safety shutdown. 

It does sound though as if the best thign to do would be to get some thermal grease and reapply the heatsink fan assembly. If you don't have thermal grease then you can really only just check that it hasn't come loose... but you may make things worse by fiddling with it.

Thermal grease isn't expensive. Any will do.

---

### Post by cipherboy_loc on 2011-02-04
Try installing AdBlock plus and removing the frame. It wasn't cooking my single core CPU, but it was close to 100% (80-90%) usage. 1.60GHz processor.



Cipherboy

---

### Post by DiSTORT3D on 2011-02-04
I have no problems at all without adblock or noscript, have allready 58 tabs open and with that one extra my cpu wont blink

---

### Post by sdowney717 on 2011-02-05
I have an E6550 core2 duo.
But it is overclocked with a standard intel cooler. 
So I ordered a Corsair A50  cooler.

And I saw it go all the way to 95 but did not notice anything else. If I had not been watching and just left it on that page, would it have self destructed?
Is flash really this bad?

---

### Post by dcstar on 2011-02-05
> **sdowney717 said:**
> [http://cgi.ebay.com/25-lbs-BURNISHING-BALLS-3-16in-65-7300-001-Polishing-/400099089380?pt=LH_DefaultDomain_0&hash=item5d27c39be4#ht_724wt_913](http://cgi.ebay.com/25-lbs-BURNISHING-BALLS-3-16in-65-7300-001-Polishing-/400099089380?pt=LH_DefaultDomain_0&hash=item5d27c39be4#ht_724wt_913)

I tested this in Firefox and Opera and it cooks my CPU
In Chrome nothing, no overheating.

So what is going on?

It is poorly written code in the advertising block at the bottom. If you move your mouse over an item and the scrolling stops, then the CPU usage also drops to normal.

Complain to eBay and the froo.com site that has provided that "feature".

---

### Post by sdowney717 on 2011-02-05
they say they will investigate further
I even linked to this page, so they know it affects others.
likely most people dont notice if they dont monitor their system

```
Customerscotd
Initial Question/Comment: Completing a Transaction
08:48:50 AM SystemSystem
Thank you for contacting eBay Live Help!
08:48:50 AM SystemSystem
You are successfully connected to eBay Live Help. Please hold for the next available Live Help Agent.
08:49:45 AM SystemSystem
We appreciate your patience. You will be able to type in your question as soon as you are connected with a Live Help Agent. Please continue to hold for the next available representative.
08:50:25 AM SystemSystem
Maricel C. has joined this session!
08:50:25 AM SystemSystem
Connected with Maricel C.
08:50:31 AM Customerscotd
hello
08:50:35 AM AgentMaricel C.
Hello, thanks for waiting and welcome to eBay Live Help! My name is Maricel. May I have your first name, please?
08:50:40 AM Customerscotd
scott
08:50:55 AM AgentMaricel C.
Hi, Scott!
08:50:55 AM AgentMaricel C.
How may I help you today?
08:51:28 AM Customerscotd
This web page on the scrolling advertisement causes my PC to fail, the CPU heats up to boiling
08:51:55 AM Customerscotd
the page is
08:51:57 AM Customerscotd
http://cgi.ebay.com/25-lbs-BURNISHING-BALLS-3-16in-65-7300-001-Polishing-/400099089380?pt=LH_DefaultDomain_0&hash=item5d27c39be4#ht_724wt_913
08:52:14 AM Customerscotd
it is due to the scrolling add at the bottom
08:54:05 AM AgentMaricel C.
You would like to report the above page because it caused your computer to heat up. Is that correct?
08:54:37 AM Customerscotd
yes, I also verifieid with many other usershttp://ubuntuforums.org/showthread.php?t=1681820&page=2
08:55:55 AM AgentMaricel C.
Are there other eBay issues I can check at the same time?
08:56:19 AM Customerscotd
no, but this one could cause a cpu to burn out
08:56:35 AM AgentMaricel C.
I'm sorry to hear about this. I can definitely do my best to look into your concern.
08:56:40 AM AgentMaricel C.
Please stay online while I check this for a few minutes.
08:56:43 AM Customerscotd
ok
08:57:55 AM AgentMaricel C.
Do you mean the scrolling bar from Frooition with Browse My Other Items you are talking about?
08:58:18 AM Customerscotd
yes
08:59:10 AM AgentMaricel C.
Let me check the other link you provided about the forum.
08:59:17 AM Customerscotd
ok
09:02:00 AM AgentMaricel C.
Kindly give me a little more time as I'm still checking on this for you.
09:02:06 AM Customerscotd
ok
09:03:10 AM AgentMaricel C.
Thanks for patiently waiting!
09:04:30 AM AgentMaricel C.
Scott, thanks for brigning this to our attention. I will have the pages and links you provided to be checked.
09:04:52 AM Customerscotd
thanks for looking into this
09:05:47 AM AgentMaricel C.
I see that you have been a part of the eBay community for years now. Thank you for continuing to do business with us over the years. We truly appreciate you as one of our valued and loyal members.
```

---

### Post by sdowney717 on 2011-02-16
Put in the new cooler today and temp on that page gets to 45c and no higher

Now when CPU is idling it runs at about 32c

pretty dramatic difference using the Corsair A50 cooler over the stock intel cooler

---

### Post by tgalati4 on 2011-02-16
Proper heat sinks and heat paste are essential and often overlooked.

Yes and No to "Is Flash that Bad?"  That's the reason Steve Jobs didn't allow flash on the iPhone--it hammers the processor and kills battery life, then you can't make phone calls in the afternoon.

Adobe claims that it's not Flash in itself that causes the problem, but how programmers use it.  If the CPU is not released when you don't have a "mouse-over" event, well that's bad programming--you can probably blame Adobe for not having a check and the programmer for not testing for that behavior.  Either way, Flash can bog down a web page.  It's not open source so you can't look at the code and say: "Well, here's the problem and here's a patch to fix it."

Google seems to be leaning on Adobe to fix some of these Flash problems so that Flash will run better on Google's upcoming ChromeOS tablets.

Otherwise just install AdBlock Plus, and NoScript and you won't see the ads and maybe your CPU will last a little longer.

---

