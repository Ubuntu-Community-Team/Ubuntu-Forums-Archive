---
title: "Download Speed(s)"
date: 2009-10-28
forum: General Help
---

### Post by Keikowned on 2009-10-28
Is there a reason why Ubuntu usually caps my download speed at around 100-200 kb/s. If yes, how do I go around this?

I usually get 1 mb/s on a XP desktop using the same wired connection. 

Thanks in advance.

---

### Post by QIII on 2009-10-28
Are you downloading similar files from the same source?

---

### Post by Giblet5 on 2009-10-28
> **Keikowned said:**
> Is there a reason why Ubuntu usually caps my download speed at around 100-200 kb/s. If yes, how do I go around this?

I usually get 1 mb/s on a XP desktop using the same wired connection. 

Thanks in advance.

1Mbps = 100KB/s - 10 bits per byte (approximately), so 1Mbps/10 = 100KB/s

As **QIII** implied, also make sure you're comparing apples to apples...

Ubuntu throttles nothing unless you, or the application you're using, do so explicitly.

As a network programmer that works with most Linux distributions and all of the Windows products, I can assure you that Linux will beat Windows in any fair network benchmark. Easily.

---

### Post by alphaniner on 2009-10-28
> 1Mbps = 100KB/s - 10 bits per byte (approximately), so 1Mbps/10 = 100KB/s

That's some fuzzy math.  1 Mbps=125 kB/s.  Because it's 8 bits per byte.

25% margin of error... are you an astronomer or astrophysicist?

---

### Post by Giblet5 on 2009-10-28
> **alphaniner said:**
> That's some extreme estimation.  1 Mbps=125 kB/s.

Only if you are NOT using TCP/IP or verifying transmission succeeded.

Nowadays, we have these things called "packets". It's very different from the carrier pigeons you grew up with... ;)

---

### Post by alphaniner on 2009-10-28
Strange then how my 1.5 Mbps connection generally tops out just under 190 kb/s and 125 * 1.5 = 187.5.  Must be a coincidence.

---

### Post by dj-toonz on 2009-10-28
Over heads & different line factors How many peoples sharing the connection at the same time (ADSL uses ratio 50/1 for home users, 20/1 ratio business lines , how many people downloading from the site. Ubuntu repos have gone slower for me because of Karmic coming out tomorrow for example 

that's so true, under Linux it shows the connection speed different then it does under windows in my eyes, I've got 2 connections a 50 meg Line & a 7.2 HSDPA connection, on the HSDPA connection I get around 600 kbs - 700 kbs from my downloads (various at different times of day & night) but on the Desktop I'm getting around 51200 kbs - 75000 kbs (various at from different times again) but under windows it shows up at say 5.2 up to 7.5 meg download speeds

---

### Post by Giblet5 on 2009-10-28
> **alphaniner said:**
> Strange then how my 1.5 Mbps connection generally tops out just under 190 kb/s and 125 * 1.5 = 187.5.  Must be a coincidence.

No, it isn't a coincidence. Your ISP is delivering <= 1.9Mbps when it's topping out.

Caveat: assumes MTU=1500 (standard) and low/no packet fragmentation

Cut the MTU to 576 and your browser will appear to scream, while file downloads will sloooow doooooown. Explain why that is, sparky. ;)

---

### Post by alphaniner on 2009-10-28
> Your ISP is delivering <= 1.9Mbps when it's topping out.

Then why does every speed test that measures in Mbps show me top out at 1.5?

---

### Post by Zoot7 on 2009-10-28
In my experience Ubuntu has been much better than Windows for using the full speed of my connection which is roughly 20Mb up and down. Just to give some example fiddling with speedtest and downloading and uploading large files. Here's what I got the last time I tried it.

Ubuntu - 20Mb/20Mb

XP - ~14Mb/10Mb

Vista - 5Mb/5Mb

Same Laptop, Same Internet Connection - Go figure.

Anyway, @OP
100kB/s is spot on for a 1Mb connection.

---

### Post by Giblet5 on 2009-10-28
> **dj-toonz said:**
> Ubuntu repos have gone slower for me because of Karmic coming out tomorrow for example

Yeah, and everyone will be updating over the next week...

I'm lucky. I have a 4Mb ADSL line that I share with nobody: straight from my farmhouse to the fiber trunk at the street. No other house for miles.

The modem says it peaked at 6.7Mb and troughed at 3.8Mb since it was last booted.

Life is good.

---

### Post by Giblet5 on 2009-10-28
> **alphaniner said:**
> Then why does every speed test that measures in Mbps show me top out at 1.5?

I dunno, but speed tests (eg, Toast.net) calculate based on 10bits/byte, so maybe we're ALL lying to you...

The only way to find out is to [learn about TCP/IP]("http://www.amazon.com/TCP-IP-Illustrated-1-Protocols/dp/0201633469").

---

### Post by vinutux on 2009-10-28
> **Zoot7 said:**
> In my experience Ubuntu has been much better than Windows for using the full speed of my connection which is roughly 20Mb up and down. Just to give some example fiddling with speedtest and downloading and uploading large files. Here's what I got the last time I tried it.

Ubuntu - 20Mb/20Mb

XP - ~14Mb/10Mb

Vista - 5Mb/5Mb

Same Laptop, Same Internet Connection - Go figure.

Anyway, @OP
100kB/s is spot on for a 1Mb connection.

+1 I have similer experience.... in ubuntu have more speed than windows....

---

### Post by Giblet5 on 2009-10-28
> **Zoot7 said:**
> In my experience Ubuntu has been much better than Windows for using the full speed of my connection which is roughly 20Mb up and down. Just to give some example fiddling with speedtest and downloading and uploading large files. Here's what I got the last time I tried it.

Ubuntu - 20Mb/20Mb

XP - ~14Mb/10Mb

Vista - 5Mb/5Mb

Same Laptop, Same Internet Connection - Go figure.

Anyway, @OP
100kB/s is spot on for a 1Mb connection.


Can we (all of us) come over to your house and surf? You have a much better connection. ;)

---

### Post by dj-toonz on 2009-10-28
200 meg Line, I'm jealous :). Fastest In the uK is 50 meg & 100 meg on trial (that's for home users) business leased lines talking up to 1 gig+

---

### Post by alphaniner on 2009-10-28
> maybe we're ALL lying to you...

Apparently so.  Speedtest.net allows me to select the measurement used.

1.42 Mbps / 179 kBs

You do the math.

---

### Post by QIII on 2009-10-28
At 8 bits per byte, 1b = .125B

(Now comes the computer science discussion about how that eighth bit is used, Big Endian, Little Endian...)

---

### Post by Zoot7 on 2009-10-28
> **Giblet5 said:**
> Can we (all of us) come over to your house and surf? You have a much better connection. ;)
Truth be told I'm downloading stuff on it pretty much 24/7 so i dont' think anybody else could tolerate using it while I'm on it. :p
Came to about 700GB last month. God bless uncapped, unrestricted College networks!! :)

---

### Post by alphaniner on 2009-10-28
> At 8 bits per byte, 1b = .125B

Right, but there are cases where 10bits=1byte.  My limited experience simply doesn't lead me to believe this is one of them, though Giblet claims it is.

---

### Post by Giblet5 on 2009-10-28
> **alphaniner said:**
> Apparently so.  Speedtest.net allows me to select the measurement used.

1.42 Mbps / 179 kBs

You do the math.


An ISP says 1Mbps: that's the *transport* speed. It doesn't account for protocol overhead. It fluctuates up and down, but will average around 1Mbps.

TCP/IP adds around 2 bits of overhead per byte (at MTU=1500) to handle end-to-end acknowledgement and connect/handshake overhead. Average.

So an ISP that delivers 1Mbps average transport will yield 100KB/s average real throughput that you can use or measure with your userspace application. Your NIC however will indicate that it's pumping 25% more data than is accounted-for by you.

Run a tcpdump while transferring a 1KB file. According to you, that dump file will be 1KB. This is something you can test and prove me wrong. Go on. Do it.

---

### Post by Giblet5 on 2009-10-28
> **QIII said:**
> At 8 bits per byte, 1b = .125B

(Now comes the computer science discussion about how that eighth bit is used, Big Endian, Little Endian...)

We prefer the term "Native Americans"... ;)

---

### Post by alphaniner on 2009-10-28
You obviously know more about this than I do.  All I'm doing is demonstrating what I've experienced many, many times over:

Mbps * 125 = approx. sustained top speed in kB/s reported by 'userspace' applications

Why don't you explain to me what's wrong with what I'm seeing?

---

### Post by QIII on 2009-10-28
The point is still this:

If the OP meant that he gets 1mbps on one system and 100kBps on another, the transfer rate is the same (accounting for overhead).  It's a matter of the units used in the report.

Unfortunately, the OP did not seem to differentiate between b and B.

---

### Post by Giblet5 on 2009-10-28
> **alphaniner said:**
> You obviously know more about this than I do.  All I'm doing is demonstrating what I've experienced many, many times over:

Mbps * 125 = approx. sustained top speed in kB/s reported by 'userspace' applications

Why don't you explain to me what's wrong with what I'm seeing?

Here's a simple test that you can easily perform:

Create a 10MB data file: ```
dd if=/dev/random of=10MEGFILE bs=1m count=10
```

Now, check your NIC's current transport speed and MTU ```
sudo ethtool eth0
```

Note the "Speed:" result. That's your transport speed. That, divided by 10, is the theoretical maximum transfer rate of data over that NIC interface if the MTU is 1500.

Now, send that file to yourself ```
scp 10MEGFILE `hostname`:10MEGFILE.copy
```

(use that as it is, don't use localhost)

It will tell you what your throughput was on that NIC interface.

What was the "Speed:" value and what was the MB/s from scp?

---

### Post by Giblet5 on 2009-10-28
> **QIII said:**
> The point is still this:

If the OP meant that he gets 1mbps on one system and 100kBps on another, the transfer rate is the same (accounting for overhead).  It's a matter of the units used in the report.

Unfortunately, the OP did not seem to differentiate between b and B.


True, and your first post was the most relevant.

One must compare apples to apples.

---

### Post by alphaniner on 2009-10-28
That didn't work, I guess because I don't have an ssh server running:

```

$ scp 10MEGFILE `hostname`:10MEGFILE.copy
ssh: connect to host caddywompus port 22: Connection refused
lost connection

```

---

### Post by Giblet5 on 2009-10-28
> **alphaniner said:**
> That didn't work, I guess because I don't have an ssh server running:

```

$ scp 10MEGFILE `hostname`:10MEGFILE.copy
ssh: connect to host caddywompus port 22: Connection refused
lost connection

```

Yep, no server...

Anyway, at 100Mbps, you can expect 7-9MB/s through the NIC interface which will perform the packetizing/depacketizing of the stream.

The fact that you'll never actually reach 10MB/s is due to the slight overhead of making the NIC operate in full duplex (simultaneous upload/download) mode.

And the 12.5MB/s that you would expect if you ignored protocol overhead is completely impossible, even using UDP instead of TCP.

QIII is right. The OP never differentiated between bits and bytes.

We are an argumentative crowd. So there's that.

---

