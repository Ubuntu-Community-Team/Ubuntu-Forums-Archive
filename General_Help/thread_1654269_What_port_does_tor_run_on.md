---
title: "What port does tor run on"
date: 2010-12-28
forum: General Help
---

### Post by ki4jgt on 2010-12-28
I'm trying to find the port which tor's website told me to put directly into firefox if I didn't use the torbutton. I found it a while back but I had to change the proxy for a bit to something else.
I've tried: 9050
I've tried: 8118
I've tried: 8080

I believe the port I am looking for has a 7 or 3 in it. Sorry I can't be very descriptive.

Already got this response from Yahoo Answers:
Check this part of the FAQ "Do I have to open all these outbound ports on my firewall?"

That would be a yes. I already read that. The port I'm refering to may have something to do with polipo or privoxy. I've already typed it in once, so I know it works. I have just forgotten what port it is. I got it off of tor's site, But I don't know what to do now, b/c all I can find, are the one's mentioned above.

Additional Details
I believe it also dealt with socks5 but not for sure. It's been forever ago.

---

### Post by Joe of loath on 2010-12-28
Start the TOR server and it will be on the control page that appears.

---

### Post by ki4jgt on 2010-12-28
How do I get that, b/c If it's in the GUI, I've searched every inch of the GUI and all it keeps telling me is 8118.

---

### Post by Joe of loath on 2010-12-28
Sorry, was confusing it with i2p. Here's the output I get from starting TOR on Arch Linux:

```
[root@tesla-biscuit joe]# tor
Dec 28 13:47:18.984 [notice] Tor v0.2.1.28 (r6e5496a2407ee589). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Dec 28 13:47:18.984 [warn] Skipping obsolete configuration option 'Group'
Dec 28 13:47:18.985 [notice] Initialized libevent version 1.4.14b-stable using method epoll. Good.
Dec 28 13:47:18.985 [notice] Opening Socks listener on 127.0.0.1:9050

```

Which displays the port used for the socks proxy, in this case 9050. Launch TOR from the terminal and see what yours says.

---

### Post by ki4jgt on 2010-12-28
It's reading 9050, but I've already tried 9050. FF won't take it. Every time I've installed tor, I've used this setting, which is a total of twice before now but each time, I seem to be the only person who can find it. I may have gotten it from Google last time. I'll see what I can do there.

---

### Post by endotherm on 2010-12-28
well, tor uses a local port for your local tunnel endpoint, so if tor is running, you can find it's port with:
```
netstat -ntlup
```

---

### Post by Joe of loath on 2010-12-28
Have you double checked the proxy setup? Socks proxies are tricky to set up in firefox. I think I resorted to using foxyproxy for mine.

---

### Post by ki4jgt on 2010-12-29
> **Joe of loath said:**
> Have you double checked the proxy setup? Socks proxies are tricky to set up in firefox. I think I resorted to using foxyproxy for mine.

It worked fine before. All I had to do was put in 127.0.0.1 and the port and use it with all protocols.

---

### Post by endotherm on 2010-12-29
you have privoxy/videlia installed and running right? privoxy runs on 9050, and proxies onto tor.

---

### Post by ki4jgt on 2010-12-29
> **endotherm said:**
> you have privoxy/videlia installed and running right? privoxy runs on 9050, and proxies onto tor.

I have privoxy. I have setup tor as per tor's website instructions (Even adding the config file to privoxy from tor's website). I put 9050 into Firefox's port and 127.0.0.1 into the proxy settings I checked apply to all services or however it's worded. The proxy server is refusing connections is all I get. Anyone have any ideas?

---

### Post by endotherm on 2010-12-29
> **ki4jgt said:**
> I have privoxy. I have setup tor as per tor's website instructions (Even adding the config file to privoxy from tor's website). I put 9050 into Firefox's port and 127.0.0.1 into the proxy settings I checked apply to all services or however it's worded. The proxy server is refusing connections is all I get. Anyone have any ideas?

so you can see your network status from within videlia right? does everything look good there?

I usually use torbutton or foxyproxy to connect firefox to a running tor instance, but there is no reason it shouldn't act as you expect.

lets check the connectivity of 127.0.0.1:9050.

run this command:
```
telnet 127.0.0.1 9050
```

if the response looks like this, then the port is open and accepting connections:
```

Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

```

but if you get a message like this, then the port is not opened, or is being blocked by the firewall:

```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

---

### Post by ki4jgt on 2010-12-29
> **endotherm said:**
> so you can see your network status from within videlia right? does everything look good there?

I usually use torbutton or foxyproxy to connect firefox to a running tor instance, but there is no reason it shouldn't act as you expect.

lets check the connectivity of 127.0.0.1:9050.

run this command:
```
telnet 127.0.0.1 9050
```

if the response looks like this, then the port is open and accepting connections:
```

Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

```

but if you get a message like this, then the port is not opened, or is being blocked by the firewall:

```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

jesse@Remember:~$ telnet 127.0.0.1 9050
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

---

### Post by endotherm on 2010-12-29
do you get the same for 8118 ( privoxy http port)?

---

### Post by ki4jgt on 2010-12-30
> **endotherm said:**
> do you get the same for 8118 ( privoxy http port)?

Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

---

### Post by endotherm on 2010-12-30
well, if you configured privoxy as they did [here]("https://help.ubuntu.com/community/Tor?action=show&redirect=TOR") (it sounds like you did), then privoxy should be providing a socks proxy on 9050 (which you confirmed is open and accepting connections) so in that case, your problem is likely client configuration. 

the ubuntu community documentation for TOR recomends TorButton, a firefox addin for toggling proxy configuration to point to tor. It's usually worked well for me. Theres another addin called external IP that can be helpful in confirming that everything is working.

the only warning I would give you on manual proxy configuration woudl be to make sure you match the socks versions. if privoxy is configured for v4, make sure the client is to. other than that, it looks like everything should be running fine.

---

### Post by ki4jgt on 2010-12-31
> **endotherm said:**
> well, if you configured privoxy as they did [here]("https://help.ubuntu.com/community/Tor?action=show&redirect=TOR") (it sounds like you did), then privoxy should be providing a socks proxy on 9050 (which you confirmed is open and accepting connections) so in that case, your problem is likely client configuration. 

the ubuntu community documentation for TOR recomends TorButton, a firefox addin for toggling proxy configuration to point to tor. It's usually worked well for me. Theres another addin called external IP that can be helpful in confirming that everything is working.

the only warning I would give you on manual proxy configuration woudl be to make sure you match the socks versions. if privoxy is configured for v4, make sure the client is to. other than that, it looks like everything should be running fine.

Is there not a way to scan for the port at all? Even if I have to do port by port? I had the port before, but now it's really bothering me. :-(

---

