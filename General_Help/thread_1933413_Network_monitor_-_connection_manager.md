---
title: "Network monitor - connection manager"
date: 2012-02-29
forum: General Help
---

### Post by minaev on 2012-02-29
Hello,

I am looking for a tool that would be able to manage network connections, like `htop' can manage processes: kill them or block permanently. Do such tools exist?

---

### Post by Ms. Daisy on 2012-03-01
You want something in terminal? Such a thing probably exists but I don't know about it because it's so easy in the GUI.

You can manage network connections by clicking on the network applet. It will list all the available wireless networks. As far as I know, Ubuntu will only connect to a network that you choose  from the list. Once it's chosen, Ubuntu will automatically connect to it  in the future.  You can click on "edit connections" and see all the wireless connections that you've used in the past.  If you don't want to automatically connect to it you can delete it from the list. 

To kill a network connection you'd just click on the applet and choose 'disconnect'.

Is that what you're after?

---

### Post by minaev on 2012-03-02
Thank you, Ms.Daisy. No, I was rather talking about established TCP connections than wifi connections. I have seen some htop-like network monitors — iftop, iptraf, nethogs. But all they can do is to display the list established connections, sorted by some counter. 

I have also found a couple of tools to kill existing connections — tcpkill and cutter (called tcp-cutter in some distributions). 

So, the tool I'd like to find would merge the features of a htop-like monitor and a connection-killer :) Yes, ideally it should be console-based and run on a gateway, displaying connections between local workstations and external hosts. Sorry if I'm asking too much :)

---

### Post by Ms. Daisy on 2012-03-02
Oh- Ha! I completely misunderstood you.  I think iptables will do that but I don't know what syntax you'd need. 
```
man iptables
```
netstat will list all the established & listening connections but I don't think you can edit connections with it.

---

### Post by raja.genupula on 2012-03-02
yeah +1 , I think we don't have a common application for Monitoring and connection management . 

Actually a discussion already done on this . read that for more info .
[http://www.cyberciti.biz/howto/question/linux/kill-tcp-connection-using-linux-netstat.php](http://www.cyberciti.biz/howto/question/linux/kill-tcp-connection-using-linux-netstat.php)

---

