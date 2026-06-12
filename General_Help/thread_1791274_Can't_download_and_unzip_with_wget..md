---
title: "Can't download and unzip with wget."
date: 2011-06-26
forum: General Help
---

### Post by laurieturpin on 2011-06-26
Hello

I'm running a unbuntu server 11.04
I am trying to download and unzip a file from sourceforge
The thing is the url of the file appears to be the following:

[http://sourceforge.net/projects/getid3/files/...1.x/getid3-1.9.0/getid3-1.9.0-20110620.zip/download](http://sourceforge.net/projects/getid3/files/...1.x/getid3-1.9.0/getid3-1.9.0-20110620.zip/download)

It is the download at the end that is giving me the problem?

I have tried downloading the file using the following 

wget [http://sourceforge.net/projects/getid3/files/...1.x/getid3-1.9.0/getid3-1.9.0-201110620.zip/download](http://sourceforge.net/projects/getid3/files/...1.x/getid3-1.9.0/getid3-1.9.0-201110620.zip/download)

What I download is a file called download.
 
When I try to unzip the file called download using:

unzip download

I get a message that says download is not a zip file.

How do I download the file I want?


Thanking you in anticipation

---

### Post by TeoBigusGeekus on 2011-06-26
```
wget http://sourceforge.net/projects/getid3/files/getID3\(\)%201.x/1.9.0/getid3-1.9.0-20110620.zip/download
unzip download
```
Notice that you have to escape the parentheses.

---

### Post by WorMzy on 2011-06-26
Try this:
```
wget "http://downloads.sourceforge.net/project/getid3/getID3%28%29%201.x/1.9.0/getid3-1.9.0-20110620.zip"
```

In the future, always use direct links for files, rather than request handling urls. Sourceforge offers you a direct link [here]("http://img8.imageshack.us/img8/3982/directq.jpg").

---

### Post by laurieturpin on 2011-06-29
Thank you for your replies TeoBigusGeekus and WorMzy. I had problems when I tried both, but that maybe because I made typo errors, perhaps. In the end I cheated and used my Windows  PC to copy the file onto usb stick and then put  the usb stick into the usb socket of my Ubuntu Server and copied the file to the server.

---

### Post by WorMzy on 2011-06-29
Is this a virtual terminal-only server? If so, I can offer you some advice regarding that. Install screen and w3m. w3m is a text-base web browser, and screen lets you copy and paste text from one buffer to another.

So you can launch screen, run w3m in one buffer, browse to the forums and copy the command me or Teo provided, then either close w3m or open a new buffer, and paste the command. It's a nice and easy way of copying a command with no chance of spelling mistakes.

Ctrl+a, then c, creates a new buffer in screen.
Ctrl+a, then 0-9, switches to different buffers (first buffer is 0).
Ctrl+a, then ESC, puts screen into copy text mode.
Ctrl+a, then ], pastes the copied text.

---

### Post by Habitual on 2011-06-29
wget [http://sourceforge.net/projects/getid3/files/...1.x/getid3-1.9.0/getid3-1.9.0-201110620.zip/download](http://sourceforge.net/projects/getid3/files/...1.x/getid3-1.9.0/getid3-1.9.0-201110620.zip/download)

will NEVER work.
Goto the SF download page in Firefox and start the download, once the download starts press Ctrl+Shift+Y and right mouse click the downloading file and select "Copy Download link".
Cancel the download in Firefox. Open your terminal do what/where you need to do/go,  you can "wget" +Shift+Insert and you'll have the real download link on the c-li.

---

