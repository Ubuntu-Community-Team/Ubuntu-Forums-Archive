---
title: "&quot;Predictable TCP Initial Sequence Number&quot; problem"
date: 2011-09-26
forum: General Help
---

### Post by coolx on 2011-09-26
Hello
I am using ubuntu, v(2.6.38-8-generic-pae). When I search my computers security bugs, there is one warning, "Predictable TCP Initial Sequence Number". When I search on the internet, I found a fix but it is no longer downloadable.

[http://www.securityfocus.com/bid/670/solution](http://www.securityfocus.com/bid/670/solution)

Is there any solution for this security vulnerability?

---

### Post by Dangertux on 2011-09-26
> **coolx said:**
> Hello
I am using ubuntu, v(2.6.38-8-generic-pae). When I search my computers security bugs, there is one warning, "Predictable TCP Initial Sequence Number". When I search on the internet, I found a fix but it is no longer downloadable.

[http://www.securityfocus.com/bid/670/solution](http://www.securityfocus.com/bid/670/solution)

Is there any solution for this security vulnerability?

Heh -- I really wouldn't worry about that , that vulnerability is from 1999 involving kernel 2.2. You are using kernel 2.6.38-8, what application said you had this problem? I'm guessing since you got a security focus link it was either Nessus or OpenVAS [http://www.securityfocus.com/bid/670/info](http://www.securityfocus.com/bid/670/info)

If you would like to see what your TCP prediction sequence looks like you can download nmap

```

sudo apt-get install nmap

```then run

```

sudo nmap -T4 -sS -sV -v -O -PN localhost

```You will see your TCP Sequencing Prediction Rate toward the bottom, and it will likely be in the 200's or close to and should look something like this

```

TCP Sequence Prediction: Difficulty=205 (Good luck!)
IP ID Sequence Generation: All zeros

```

---

### Post by coolx on 2011-09-26
Firstly thanks for your answer. The application's name is Nexpose. So I didnt worry about this vulnerability:)

---

