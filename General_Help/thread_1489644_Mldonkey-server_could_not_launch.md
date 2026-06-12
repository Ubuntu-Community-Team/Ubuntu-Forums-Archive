---
title: "Mldonkey-server could not launch"
date: 2010-05-21
forum: General Help
---

### Post by huangyingw on 2010-05-21
Hello all,
	I found my mldonkey-server curiously could not launch after rebooting:(
	To confirm my suspicion, after the following command:
	```

	root@Mldonkey:~# /etc/init.d/mldonkey-server start
	Starting MLDonkey: mlnet.
	
```
	I run 
	```

	root@Mldonkey:~# telnet localhost 4000
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@Mldonkey:~# 
	
```
	And what is more:
	```

	root@Mldonkey:~# ps ax|grep mld
 1914 pts/0    S+     0:00 grep mld
root@Mldonkey:~# 
	
```
	I have tried reinstalling, but still the same situation:(

---

### Post by tkhobbes on 2010-06-08
Hi - same problem here, did you find a solution?

---

### Post by huangyingw on 2010-06-08
> **tkhobbes said:**
> Hi - same problem here, did you find a solution?
Yes, not at home PC now. Just a rough recall, might be not exact.
I have investigated this. Seems that the files.ini or some related small files corrupted.
Some real-time overwritting small files would intended to be corrupted. And this seems to happen when rebooting or shutdowning PC.
So, my solution is re-write my own "reboot" command: stop the mldonkey server first, then use git commit to save the current small files(or any way you like to save them), and finally reboot. 
After this updating, my mldonkey never go wrong now:)
Good luck to you

---

### Post by tkhobbes on 2010-06-09
Hi - thanks but I don't understand... I checked, files.ini seems ok... I deleted all files that were currently being downloaded and emptied the temp directory - still, it does not work... :(

---

### Post by huangyingw on 2010-06-09
> **tkhobbes said:**
> Hi - thanks but I don't understand... I checked, files.ini seems ok... I deleted all files that were currently being downloaded and emptied the temp directory - still, it does not work... :(
Not at home PC, so, might be not exact. You could suggest me a better way to better describe this issue:)
Hi, it is totally none of the temp and downloading files' business. It is only some small, and run-time overwriting configuration files that cause.
In order to fix this, or a simple experiment to prove what I said, you could delete all in /var/lib/mldonkey/ directory, except the temp directory. After this, you could re-install the mldonkey-server again. And it could works again.
And what is more, what you have downloaded in "temp" is still re-usable. But, when you see from the web, the downloading items' names are all ***** codes. This is because that the file which descript the downloading files details in "temp" directory, is deleted or corrupted.

---

### Post by tkhobbes on 2010-06-11
Hi - did that (removed mldonkey completely and reinstalled it) - same story. :(

---

### Post by huangyingw on 2010-06-12
> **tkhobbes said:**
> Hi - did that (removed mldonkey completely and reinstalled it) - same story. :(
So, your procedure is
1. apt-get remove mldonkey-server
2. rm -frv /var/lib/mldonkey
3. apt-get install mldonkey-server
?
If yes, and still the same story. Sorry, I could not help you now..

---

### Post by tkhobbes on 2010-06-15
well - for whatever reasons, it worked again. Don't ask why.... I removed (again) and reinstalled... now it seems to work fine :)

---

