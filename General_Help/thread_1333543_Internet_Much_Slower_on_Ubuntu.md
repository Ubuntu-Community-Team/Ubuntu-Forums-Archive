---
title: "Internet Much Slower on Ubuntu"
date: 2009-11-21
forum: General Help
---

### Post by ukapolog on 2009-11-21
Okay, I'll come clean. I have really fallen in love with Ubuntu, even though I am quite a supporter of Windows Vista and reject a lot of the criticism that it has had. I think Ubuntu 9.10 is superb except for a few little moans. For example, why can't one change that dreadful brown  login screen?? Apparently on earlier versions of Ubuntu one could but no longer unless one is a techo genius (which I am most certainly not).

But I do have quite a major 'beef' and doing a Google search I find that other Ubuntu people have the same problem. The internet is often pathetically slow compared with Windows. On Ubuntu I really like Konqueror and I also use Firefox but both are often very slow. Yet when I switch to Windows Vista,  Firefox, as well as IE8 and Chrome just fly. I use a powerful computer and have a fast net speed but for some reason Ubuntu, for all it's smashing bits, cannot take advantage of them.

Any possible solution? If one is offered please make it very clear for a non-genius.

Thanks.

---

### Post by Dennis N on 2009-11-21
If you mean slow to resolve web sites, I believe that is a DNS problem. As I understand it from various other posts, Ubuntu in Karmic first tries to find an IPv6 address for websites causing a delay of several seconds, then falls back to Ipv4 when the first attempt fails (because there is no IPv6 address yet). This affects all applications with web access. On a web page with lots of content from different sources, this slows things down considerably.

Once connected, as in doing a download, speed can still be normal.

---

### Post by ukapolog on 2009-11-21
Hi there.
Thank you for that. You say,
 
>  
Once connected, as in doing a download, speed can still be normal

 
I am a comparative newby but that is not what I find.

---

### Post by Dennis N on 2009-11-21
If the download speed (such as when downloading updates) is slow, that may be demands on the server, or just general internet traffic conditions. Hard to tell. 

The DNS issue (if you think you have it) might be helped by disabling ipv6 in Firefox. If you want to do that (I did) type:

```
about:config
```

in the Firefox address bar. Click "I'll be careful" then look for 

```
network.dns.disableIPv6
```

click twice (I think) on the line and the value should change from "false" to "true" at the end.

---

### Post by Uncle Spellbinder on 2009-11-21
> **Dennis N said:**
> If the download speed (such as when downloading updates) is slow, that may be demands on the server, or just general internet traffic conditions. Hard to tell. 

The DNS issue (if you think you have it) might be helped by disabling ipv6 in Firefox. If you want to do that (I did) type:

```
about:config
```

in the Firefox address bar. Click "I'll be careful" then look for 

```
network.dns.disableIPv6
```

click twice (I think) on the line and the value should change from "false" to "true" at the end.

Thanks for that. Forgot about it. Works for SeaMonkey as well, by the way.

---

### Post by sgosnell on 2009-11-21
TYou can also use OpenDNS instead of the default DNS server.  There are several threads on this forum discussing this problem and various fixes.

---

### Post by coffeecat on 2009-11-21
The IPv6/DNS issue in Karmic only affects a minority of users, but is a major problem if it hits you. [This launchpad thread]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757") has most of the gory details. Post #7 is interesting.

But if this is the issue that's hit you, disabling IPv6 in Firefox is only going to fix Firefox. Anything else on the system will still be affected. You need a system-wide solution - at least until a bug-fix is released. Have a look at post #72 for how to disable IPv6 globally via grub2.

But we need to exclude other reasons for your slow internet speed. **ukapolog**, you haven't given us any details of your network. Is the connection between your computer and router wireless or wired? And what make and model is your router? If wireless, you may have a chipset with a buggy driver in Karmic. We need to exclude that as a possibility. What wireless device (if any) are you using?

---

### Post by wojox on 2009-11-21
```

1.  Press ALT + F2 to open the "Run Application" window
2. Paste "gksudo gedit /etc/default/grub" in the command box
3. Tick "Run in terminal" and press "Run"
4. Type your password in the Terminal
5. In the text editor that opens, replace "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" with "GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash""
6. Open a Terminal and paste "sudo update-grub"
7. Restart your computer for the effects to take place

```

---

### Post by sgosnell on 2009-11-21
For a system-wide fix (at least on a network-by-network basis) without futzing with GRUB, try [ the instructions on this page](https://store.opendns.com/setup/device/ubuntu/).  It will let you use OpenDNS servers, and it worked well for me.

---

### Post by ManiacMagee on 2009-11-22
I recently upgraded to Karmic and had the same issue.  Dennis N's suggestion fixed my problem for Firefox, and the system-wide solution mentioned by coffeecat and wojox worked for other programs.  If anyone else has this issue after upgrading (rather than a clean install), you may have to edit the "quiet splash" line of "/boot/grub/menu.lst" rather than "/etc/default/grub".  

Thanks for posting the fixes.

---

### Post by Palumbo on 2009-12-30
> **wojox said:**
> ```

1.  Press ALT + F2 to open the "Run Application" window
2. Paste "gksudo gedit /etc/default/grub" in the command box
3. Tick "Run in terminal" and press "Run"
4. Type your password in the Terminal
5. In the text editor that opens, replace "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" with "GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash""
6. Open a Terminal and paste "sudo update-grub"
7. Restart your computer for the effects to take place

```


I think this thread has a lot of very accurate information. I'm running Ubuntu 9.10 installed on a ThinkPad T43 using the Wubi installer. Firefox running on Windows XP Professional has excellent response time whereas Firefox running in Karmic is painfully slow. 

I ran a speed test on both of them using [http://speakeasy.net/speedtest](http://speakeasy.net/speedtest). 

Firefox + Windows XP Pro downloaded at 18972 kbps

Firefox + Ubuntu 9.10 downloaded at 25130 kbps

A sizable difference on paper, but in no way representative of the actual download speeds. 

Alright, now for my question. I believe that Karmic's predilection to resolved IPV6 addresses before falling back to the more common IPv4 is the root of the problem. I was able to modify about:config in Firefox to remedy the problem for that one application, but when I tried the modify /etc/default/grub I noticed that I do not have that file - probably because I used the Wubi installer. 

Any ideas on how I might be able to modify Ubuntu's IPv6 preference? 

Thanks, 
Palumbo

---

