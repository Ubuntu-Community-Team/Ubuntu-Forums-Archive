---
title: "Gmail users please post connection information"
date: 2010-08-30
forum: General Help
---

### Post by Rumpletumbler on 2010-08-30
I have an issue in Gmail that has just started recently. When I'm logged into Gmail I sometimes have as many as 22-28 outbound connections and my NIC never stops sending and receiving data.

When I log into Gmail this starts and doesn't stop even if I log out and close the tab. I have to quit the browser to lose the connections.

Here's what my connectivity is without Firefox running. 

```
COMMAND     PID    USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
avahi-dae   595   avahi   13u  IPv4    3911      0t0  UDP *:5353 
avahi-dae   595   avahi   14u  IPv4    3912      0t0  UDP *:52683 
privoxy     877 privoxy    1u  IPv4    4470      0t0  TCP 127.0.0.1:8118 (LISTEN)
sendmail-  1152    root    4u  IPv4    5166      0t0  TCP 127.0.0.1:25 (LISTEN)
sendmail-  1152    root    5u  IPv4    5167      0t0  TCP 127.0.0.1:587 (LISTEN)
cupsd      1287    root    5u  IPv6 3465625      0t0  TCP [::1]:631 (LISTEN)
cupsd      1287    root    6u  IPv4 3465626      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  20014    root    5u  IPv4 2884938      0t0  UDP *:68
```


This is logged into Gmail. 

```
COMMAND     PID    USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
avahi-dae   595   avahi   13u  IPv4    3911      0t0  UDP *:5353 
avahi-dae   595   avahi   14u  IPv4    3912      0t0  UDP *:52683 
privoxy     877 privoxy    1u  IPv4    4470      0t0  TCP 127.0.0.1:8118 (LISTEN)
privoxy     877 privoxy    2u  IPv4 4127084      0t0  TCP 127.0.0.1:8118->127.0.0.1:32960 (ESTABLISHED)
privoxy     877 privoxy    3u  IPv4 4129597      0t0  TCP 127.0.0.1:8118->127.0.0.1:32975 (ESTABLISHED)
privoxy     877 privoxy    4u  IPv4 4127123      0t0  TCP 127.0.0.1:8118->127.0.0.1:32963 (ESTABLISHED)
privoxy     877 privoxy    5u  IPv4 4127176      0t0  TCP 192.168.1.104:55694->74.125.65.105:443 (ESTABLISHED)
privoxy     877 privoxy    6u  IPv4 4127903      0t0  TCP 192.168.1.104:46604->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy    7u  IPv4 4127307      0t0  TCP 127.0.0.1:8118->127.0.0.1:32965 (ESTABLISHED)
privoxy     877 privoxy    8u  IPv4 4127310      0t0  TCP 127.0.0.1:8118->127.0.0.1:32967 (ESTABLISHED)
privoxy     877 privoxy    9u  IPv4 4127317      0t0  TCP 192.168.1.104:46598->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   10u  IPv4 4129600      0t0  TCP 192.168.1.104:46606->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   11u  IPv4 4129663      0t0  TCP 127.0.0.1:8118->127.0.0.1:32976 (ESTABLISHED)
privoxy     877 privoxy   12u  IPv4 4127387      0t0  TCP 127.0.0.1:8118->127.0.0.1:32973 (ESTABLISHED)
privoxy     877 privoxy   13u  IPv4 4127390      0t0  TCP 192.168.1.104:46602->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   14u  IPv4 4129665      0t0  TCP 127.0.0.1:8118->127.0.0.1:32977 (ESTABLISHED)
privoxy     877 privoxy   15u  IPv4 4129667      0t0  TCP 127.0.0.1:8118->127.0.0.1:32981 (ESTABLISHED)
privoxy     877 privoxy   16u  IPv4 4130365      0t0  TCP 192.168.1.104:46612->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   17u  IPv4 4129915      0t0  TCP 192.168.1.104:46610->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   18u  IPv4 4130165      0t0  TCP 192.168.1.104:46611->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   20u  IPv4 4135257      0t0  TCP 192.168.1.104:45010->74.125.67.189:443 (ESTABLISHED)
sendmail-  1152    root    4u  IPv4    5166      0t0  TCP 127.0.0.1:25 (LISTEN)
sendmail-  1152    root    5u  IPv4    5167      0t0  TCP 127.0.0.1:587 (LISTEN)
cupsd      1287    root    5u  IPv6 3465625      0t0  TCP [::1]:631 (LISTEN)
cupsd      1287    root    6u  IPv4 3465626      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  20014    root    5u  IPv4 2884938      0t0  UDP *:68 
firefox-b 23965    username   46u  IPv4 4135253      0t0  TCP 127.0.0.1:32981->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   55u  IPv4 4127303      0t0  TCP 127.0.0.1:32963->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   60u  IPv4 4127122      0t0  TCP 127.0.0.1:32960->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   63u  IPv4 4129596      0t0  TCP 127.0.0.1:32973->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   64u  IPv4 4127309      0t0  TCP 127.0.0.1:32965->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   65u  IPv4 4127320      0t0  TCP 127.0.0.1:32967->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   66u  IPv4 4129662      0t0  TCP 127.0.0.1:32975->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   67u  IPv4 4129664      0t0  TCP 127.0.0.1:32976->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   68u  IPv4 4129666      0t0  TCP 127.0.0.1:32977->127.0.0.1:8118 (ESTABLISHED)
```

This has not been happening until recently to my knowledge. I know the number of connections is 5-7 times what is normal. 

Can someone take a look at their connection information logged into Gmail and see if you are experiencing the same thing? 

I had a thread [http://ubuntuforums.org/showthread.php?t=1563561](http://ubuntuforums.org/showthread.php?t=1563561) that initially was about this issue but I didn't know it seemed to be totally Gmail related so I thought I might ask this way. It could be Google just changed something on their end but I don't want to run my mail until I know it's ok.

---

### Post by CharlesA on 2010-08-30
Was it after you started using the proxy?

---

### Post by Rumpletumbler on 2010-08-30
> **CharlesA said:**
> Was it after you started using the proxy?

No, Privoxy has been installed a while. The only new thing that I put on near the time it seemed to start was Ghostery but I disabled that as well as all other plugins one at a time and the behavior remained.

I'm running Ghostery, NoScript, Optimize Google and FlashVideoReplacer.

---

### Post by CharlesA on 2010-08-30
Try disabling all the add-ons and see if the same thing happens.

---

### Post by Rumpletumbler on 2010-08-30
> **CharlesA said:**
> Try disabling all the add-ons and see if the same thing happens.

Disabled all the extensions and all the plug-ins and restarted Firefox. 

Logged into Gmail and there's no difference. 

[IMG]http://img691.imageshack.us/img691/9343/screenshot1fv.png[/IMG]

---

### Post by The Cog on 2010-08-30
I don't know if it's significant or relevant, but something changed in googlemail.com in the UK recently - IIRC it stopped accepting imaps connections, but other things may have changed too. I fixed it by changing to connect to gmail.com instead of googlemail.com.

---

### Post by uRock on 2010-08-30
I use thunderbird for gmail, so that I do not have to go to their site. Do you have UPnP enabled on your router? Disabling may help prevent this.

---

### Post by Rumpletumbler on 2010-08-30
> **uRock said:**
> I use thunderbird for gmail, so that I do not have to go to their site. Do you have UPnP enabled on your router? Disabling may help prevent this.

I'll have to take a look. It isn't my router and I doubt the guy who owns it would have changed anything but I'll look when I can round him up and see.

---

### Post by Rumpletumbler on 2010-08-30
> **uRock said:**
> I use thunderbird for gmail, so that I do not have to go to their site. Do you have UPnP enabled on your router? Disabling may help prevent this.

Disabled without result. 

Just going to the gmail login starts a constant stream of up and down on the NIC and opens 10 outbound connections.

---

### Post by uRock on 2010-08-30
> **Rumpletumbler said:**
> Disabled without result. 

Just going to the gmail login starts a constant stream of up and down on the NIC and opens 10 outbound connections.
Eeek! Not good.

---

### Post by Rumpletumbler on 2010-08-30
> **uRock said:**
> Eeek! Not good.

Weird. 

So anyway, now this board is acting up.

When I try to go the usercp I get:

[IMG]http://img829.imageshack.us/img829/7226/screenshot2pi.png[/IMG]

Then I got a permissions error. 

Now it works. 

Something is amiss.

---

### Post by Rumpletumbler on 2010-08-31
Nothing changed from a fresh install so it must be google.

---

### Post by malspa on 2010-08-31
Can you tell what to run to get the type of output shown in post #1 as well as in post #5?  Thanks.

---

### Post by ivikas on 2010-08-31
Hello


> 
privoxy     877 privoxy    2u  IPv4 4127084      0t0  TCP 127.0.0.1:8118->127.0.0.1:32960 (ESTABLISHED)
privoxy     877 privoxy    3u  IPv4 4129597      0t0  TCP 127.0.0.1:8118->127.0.0.1:32975 (ESTABLISHED)



I don't know exactly but i think privoxy is running and it's a web filtering tool 
installed in firewalls to filter or block web contents.

You can get more information here.

```

http://www.privoxy.org/

```

---

### Post by Rumpletumbler on 2010-08-31
> **malspa said:**
> Can you tell what to run to get the type of output shown in post #1 as well as in post #5?  Thanks.

 I found it somewhere here in another post and since I rebuilt my system I don't have it anymore. I'll look and see if I can find it again.  Edit: I believe it was lsof but don't recall the switches. man lsof should help.

I think it was 

```
sudo lsof -n -i -P
```

---

### Post by Rumpletumbler on 2010-08-31
> **ivikas said:**
> Hello





I don't know exactly but i think privoxy is running and it's a web filtering tool 
installed in firewalls to filter or block web contents.

You can get more information here.

```

http://www.privoxy.org/

```

 Yes, I run Privoxy. This behavior is present with or without Privoxy.

---

### Post by Rumpletumbler on 2010-08-31
I don't get the constant traffic over the NIC from a Windows box while logged in.

As I have scratched this machine and rebuilt it must be something unique to Linux? Ubuntu?

Anyone have any idea? Theory? WAG?

Can anyone running Lucid Lynx and Firefox with a Gmail account see if this is happening with them please?

---

### Post by Rumpletumbler on 2010-09-01
bump

---

### Post by uRock on 2010-09-01
I just visited the Gmail site in Firefox with Wireshark running and I am thinking that all of the different in window applications have their own connection, such as the chat applet and the make a phone call applet, amongst other things. I think this goes to show how busy the gmail page is and why I am glad I usually use Thunderbird to access my email.

Final conclusion is that it is normal for gmail to open so many ports.

---

### Post by Rumpletumbler on 2010-09-01
> **uRock said:**
> I just visited the Gmail site in Firefox with Wireshark running and I am thinking that all of the different in window applications have their own connection, such as the chat applet and the make a phone call applet, amongst other things. I think this goes to show how busy the gmail page is and why I am glad I usually use Thunderbird to access my email.

Final conclusion is that it is normal for gmail to open so many ports.

Were you continually passing traffic? If so then why would this exhibit itself in Linux and not Windows?

---

### Post by Rumpletumbler on 2010-09-02
Could someone please verify if you pass constant traffic while logged into Gmail. Actually just sitting at the login does the same thing. 

Thanks.

---

### Post by uRock on 2010-09-02
Wireshark show packets that keep going, then after closing the the page it stops.

---

### Post by Rumpletumbler on 2010-09-02
> **uRock said:**
> Wireshark show packets that keep going, then after closing the the page it stops.

I can have gmail opened in a tab or it be the only thing open and I have to quit the browser to loose the connections and stop passing the traffic. Closing the tab or going to a different site doesn't work.

---

### Post by Rumpletumbler on 2010-09-02
Doesn't do it on OSX either, just tested that.  Seems to be only my box or only Lucid Lynx and Firefox.

---

### Post by Saprissa on 2010-09-04
No problems here in Lucid with Firefox...


```

avahi-dae  905   avahi   13u  IPv4   4079      0t0  UDP *:5353 
avahi-dae  905   avahi   14u  IPv4   4080      0t0  UDP *:46835 
cupsd     1079    root    6u  IPv6   4433      0t0  TCP [::1]:631 (LISTEN)
cupsd     1079    root    7u  IPv4   4434      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  1544    root    5w  IPv4   8613      0t0  UDP *:68 
ubuntuone 1671 tulemar   20u  IPv4  12085      0t0  TCP 192.168.2.6:40748->91.189.89.218:443 (CLOSE_WAIT)
ubuntuone 1671 tulemar   21u  IPv4   9744      0t0  TCP 192.168.2.6:36921->174.129.241.144:443 (ESTABLISHED)
firefox-b 1689 tulemar   48u  IPv4  18135      0t0  TCP 192.168.2.6:39831->66.102.7.83:443 (ESTABLISHED)
firefox-b 1689 tulemar   66u  IPv4  18645      0t0  TCP 192.168.2.6:39841->66.102.7.83:443 (ESTABLISHED)
firefox-b 1689 tulemar   79u  IPv4  12281      0t0  TCP 127.0.0.1:33724->127.0.0.1:54384 (ESTABLISHED)
firefox-b 1689 tulemar   83u  IPv4  22470      0t0  TCP 192.168.2.6:59540->66.102.7.100:80 (ESTABLISHED)
GoogleTal 1740 tulemar   12u  IPv4  12099      0t0  TCP 127.0.0.1:54384 (LISTEN)
GoogleTal 1740 tulemar   13u  IPv4  12282      0t0  TCP 127.0.0.1:54384->127.0.0.1:33724 (ESTABLISHED)
chrome    2053 tulemar  113u  IPv4  16450      0t0  TCP 192.168.2.6:53331->74.125.155.125:5222 (ESTABLISHED)
```

---

