---
title: "internet &quot;hangs up&quot; with 9.10"
date: 2009-11-14
forum: General Help
---

### Post by boz86 on 2009-11-14
In both Firefox and Opera downloading seems to hang up frequently.

Doesn't happen with the same computer using Windows Vista.

Any pointers to troubleshooting would be appreciated. This is on a Dell laptop Inspiron 1520 and a wireless connection.

Pingtest.net shows very good connections when it's not hung up.

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
Hey man... if you have more to say on your first post then put it in the first post don't make another. Lets keep this forum tidy.

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
A quick use of the SEARCH function at the top of this page brought up this [http://ubuntuforums.org/showthread.php?p=8308454](http://ubuntuforums.org/showthread.php?p=8308454)  That search bar and Google can be great for finding solutions to many problems. Let us know if anything there worked.

---

### Post by boz86 on 2009-11-14
> **Sin@Sin-Sacrifice said:**
> Hey man... if you have more to say on your first post then put it in the first post don't make another. Lets keep this forum tidy.

Thanks.

---

### Post by boz86 on 2009-11-14
> **Sin@Sin-Sacrifice said:**
> A quick use of the SEARCH function at the top of this page brought up this [http://ubuntuforums.org/showthread.php?p=8308454](http://ubuntuforums.org/showthread.php?p=8308454)  That search bar and Google can be great for finding solutions to many problems. Let us know if anything there worked. 
OK, now I'm back on Windows, which at least works.

I had already tried the search BEFORE posting and found the IPv6 fix, which didn't work for me.

Even went to the library today and got a Ubuntu book which didn't help at all with this problem.

---

### Post by Giblet5 on 2009-11-14
> **boz86 said:**
> OK, now I'm back on Windows, which at least works.

I had already tried the search BEFORE posting and found the IPv6 fix, which didn't work for me.

Even went to the library today and got a Ubuntu book which didn't help at all with this problem.


OK, I suspect this is a either a gag or a fanboy prank, but I'll play along for a minute or two...

What makes you think the internet is hanging?

Obviously, something happened - or failed to happen - that led you to believe that internet traffic is halting at your door. What was it?

Did that ... event ... just start occurring, or is it behavior that appears to be a constant with Ubuntu?

Can you reproduce the behavior? How? Explain the exact steps.

What have you done to diagnose the problem, aside from visiting a website (pingtest)?

---

### Post by boz86 on 2009-11-14
> **Giblet5 said:**
> OK, I suspect this is a either a gag or a fanboy prank, but I'll play along for a minute or two...

What makes you think the internet is hanging?

Obviously, something happened - or failed to happen - that led you to believe that internet traffic is halting at your door. What was it?

Did that ... event ... just start occurring, or is it behavior that appears to be a constant with Ubuntu?

Can you reproduce the behavior? How? Explain the exact steps.

What have you done to diagnose the problem, aside from visiting a website (pingtest)?

Ok, here's the deal. I wish I was just pranking, but I really want to get Ubuntu working. I don't have anything against Microsoft, Vista worked fine for me, but I want the increased security of Linux. Had Fedora installed previously on a desktop and it worked great. 9.04 is working on the same desktop just fine. After good experiences there I wanted to transition my laptop to Linux. 

I downloaded the Ubunta cd, installed as a dual boot on my laptop. Even gave a friend a copy of the live CD since the install seemed to go so well.

Everything went well, except Firefox "stalled" sometimes when downloading various websites. I tried Chromium but it crashed repeatedly. Then I downloaded Opera and the same issues as Firefox popped up, it worked fine for a bit then would take up to a minute or two to download pages.

Finally ended up disconnecting from my wireless connection and reconnecting. That seems to work for a "bit", then it's back to hanging up/stalling. Even had the wireless connection take three or four tries to connect.

I'm thinking the router might be an issue but I've spent hours connected with Windows today, with only an occasional delay.

---

### Post by Giblet5 on 2009-11-14
Good. I have nothing against Windows either. This system will boot XP, Vista, and Win7, along with several other OSes.

Is it possible that your ISP is throttling you?

Some ISPs will throttle your connection if you aren't using a QoS strategy via your OS or router.

Is this just your perception of things?

Windows (esp Vista) intentionally throttles all network connections (it's called QoS). This has a huge benefit in that a consistently slow connection *appears* to perform better than one which delivers faster overall throughput, but in a less consistent manner.

May I suggest a good benchmark?

Visit [www.toast.net](www.toast.net) and run their web benchmark. Choose the "Image and Text" benchmark.

If that benchmark is giving you worse (or even the same!) throughput as Windows Vista, then you have a problem with your wifi driver and we can start looking into that. Linux will always outperform Vista if everything is working correctly.

Try the benchmark a few dozen times on Windows and under Linux, and post the final numbers here.

---

### Post by boz86 on 2009-11-15
> **Giblet5 said:**
> 
Visit [www.toast.net]("http://www.toast.net") and run their web benchmark. Choose the "Image and Text" benchmark.

If that benchmark is giving you worse (or even the same!) throughput as Windows Vista, then you have a problem with your wifi driver and we can start looking into that. Linux will always outperform Vista if everything is working correctly.

Try the benchmark a few dozen times on Windows and under Linux, and post the final numbers here.

OK, starting running the tests as you suggested. Getting consistently better results in Linux than Windows (about 30% better), then it just stopped after 10 or 15 minutes of use. Even though the icon showed I still had a good connection, no pages would download (multiple different servers). I disconnected the wireless connection after about three minutes and tried to reconnect. No such luck, couldn't get the connection restored.

To back up a bit, it took me two or three tries to get the wireless to connect the first time after boot up, but it worked great for a while after that.

Argghh. So close. Couple of other noob issues but I can look those up on my own, or ask in the noob forum.

---

### Post by boz86 on 2009-11-15
> **Giblet5 said:**
> 
If that benchmark is giving you worse (or even the same!) throughput as Windows Vista, then you have a problem with your wifi driver and we can start looking into that. Linux will always outperform Vista if everything is working correctly.

I am really leaning toward the driver issue. Or I've entered an bad setting.

I have updated the router (Netgear WGR614v6, U.S.) to the latest firmware off their website.

Just as before, it takes two or three tries to get the wireless connected, and then it stops working after a few minutes. I've connected with an ethernet cable and that's working great. It's consistently faster than Windows and is maintaining a good connection.

I have the wireless settings (don't know the command to pull all of them but here's me copying them over):

Wireless: SSID set, Mode infrastructure, BSSID empty, MAC address empty, MTU automatic

Wireless Security: Security WPA and WPA 2 Personal, Password entered

IPv4 Settings: Automatic (DHCP), DHCP client ID empty, routes all empty

IPv6 Settings: Method Ignore.

Any thoughts on how to get the wireless working?

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
I had a similar problem with WPA password set. I, in stead, used the MAC address filter to only allow my phone and this PC to connect to the router when I figured out that it worked flawlessly with WPA disabled. Something you might want to consider.

---

