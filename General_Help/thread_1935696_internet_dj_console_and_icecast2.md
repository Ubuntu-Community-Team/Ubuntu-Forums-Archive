---
title: "internet dj console and icecast2"
date: 2012-03-04
forum: General Help
---

### Post by eldafani on 2012-03-04
Hi all,

I am new to ubuntu and am beginner also at setting up an internet radio station. I am trying to stream music from idjc to icecast2. 

First, I followed instructions in 

[http://www.ehow.com/how_5183447_make-radio-stream-ubuntu.html](http://www.ehow.com/how_5183447_make-radio-stream-ubuntu.html)
[http://askubuntu.com/questions/28496/how-do-i-setup-an-icecast-server-for-broadcasting-audio-in-my-network](http://askubuntu.com/questions/28496/how-do-i-setup-an-icecast-server-for-broadcasting-audio-in-my-network)

to configure icecast2 with my own username and password. Then I also followed instructions in 
 
[http://idjc.sourceforge.net/tutorials_icecast.html](http://idjc.sourceforge.net/tutorials_icecast.html)

to configure idjc and icecast2. And I am now able to log into

[http://localhost:8000/admin/](http://localhost:8000/admin/) 

using my username and password. 

The problem is that I can't get idjc to connect to the icecast server:

type: icecast 2 master
host: localhost
IP: <my own>
port: 8000
mount: /listen
login: <my own>
password: <my own>

Nothing happens when I add this server in idjc and then click on connect. Not even the yellow color appears. What am I missing?

My other question is, the stream is suppose to play in "<my IP>:8000/listen", is that correct?

I greatly appreciate your advice. Thank you.
Daniel

---

### Post by cryptotheslow on 2012-03-04
Hi Daniel,

I've been using IDJC for years but for Shoutcast rather than Icecast - so I may be able to help.

When I look at the Radio Server window setup for Icecast 2 Master I see no field for "IP:" just:
Type: Icecast 2 Master
Host:
Port: 8000
Mount:
Login:
Pass:

What version of IDJC do you have installed? (0.8.1-4ubuntu1 here)

If you have an additional field for "IP:" and as you appear to be hosting your own Icecast you'd logically enter 127.0.0.1 rather than your internet facing IP address.

Maybe a screenshot of your Radio Server window would help.

Oh - and welcome to the world of internet radio :D

~crypto~

---

### Post by acimi66 on 2012-03-04
I didn't think IDJC worked without JACK.
That's how it worked for me...eventually.

---

### Post by cryptotheslow on 2012-03-04
You are right acimi66. It requires jackd.

I remember in Ubuntu 9.10 and prior days having to create a custom launch script that first fired up the jack daemon with appropriate parameters then fired up IDJC with parameters to connect to that named jackd instance.

However, on 10.04 IDJC is in the Ubuntu multiverse repos and seems to take care of all that automagically. Now it is just a menu click application. It starts jackd transparently like this:

```
crypto@crypto-desktop:~$ ps aux | grep jack
crypto    2576  9.4  1.3  27460 27480 ?        SLsl 01:52   0:00 /usr/bin/jackd -T -ndefault -dalsa -dhw:0 -r44100 -p1024 -n2
```And I for one am glad this is so - the endless hours trying to work out what was going on with pulse, alsa, oss and jack exploded my head.

I suppose this raises another question for the OP - what version of Ubuntu do you run and how did you install IDJC?

---

### Post by acimi66 on 2012-03-04
Here's my set-up at the moment.
I have IDJC and JACK in the launcher so I don't even need to use terminal. 
My god.... it's almost like windows! HA.

I hope that helps.

---

### Post by eldafani on 2012-03-05
Hi again,

Thanks a lot for your quick replies! :) I am using Ubuntu 10.04 LTS and IDJC 0.8.1. I also have JACK installed. I should mention that I am able to stream music to an account I created at caster.fm. So I guess IDJC and JACK are not the problem. 

Attached is a screenshot of my radio server configuration for icecast2. 

When I try to connect, the yellow color appears and then the connection fails. I have tried different options in the "host" field, including my IP address and typing "localhost", but they don't work either. 

Note that I was able to change the default username/password in icecast2 and that's why I am using my own. Also, I try to connect only after starting the server with 

sudo /etc/init.d/icecast2 start

When I start the server for caster.fm online, and then try to connect with the configuration provided in the caster website, I can stream music. I cannot listen to the music on my own computer neither I can listen to any audio while running IDJC. I used another computer to make the test. 

Again, any help is very much appreciated. Thank you.
Daniel

in the terminal. 

Here is a screenshot of my Radio Server.

---

### Post by acimi66 on 2012-03-05
Well for me, JACK has to be opened THEN IDJC and I still have to CONNECT inside IDJC output.

I did notice that the parameters of your connection where not displayed in the CONNECTION BOX i.e Edit/remove        add.

---

### Post by cryptotheslow on 2012-03-05
You don't necessarily need to open the JACK graphical patchbay application - you can just fire up a jackd (JACK daemon) process in the background. Which I think is how the repo installed IDJC / JACK combination is configured to work.

If he can connect to caster.fm from IDJC then it would seem the JACK startup is working OK.

If I get the time later on I'll try installing a local icecast instance and see how it goes.

eldafani - Do you have a firewall configured and running on the PC in question?

---

### Post by eldafani on 2012-03-06
cryptotheslow - No, I don't have any firewall running. It is also not quite clear to me why streaming locally with icecast2 is "better" than with caster.fm or another service. Because if the advantages are not great I might as well stay with caster.fm. Any web references on this? Thank you.

---

### Post by cryptotheslow on 2012-03-06
If you stream to a local icecast then every person tuning in to your stream will connect directly to your PC. This can very quickly swamp your upstream bandwidth.

Using the likes of caster.fm (or any other icecast/shoutcast provider) you stream to the remote server and listeners tuning in connect to that server rather than to you. As the server is likely sat in a data centre somewhere with nice big fibre links the bandwidth consumption is relatively trivial.


Say for example you wish to broadcast your stream at 128Kbps and 8 people tune in - if you are running it yourself you already need a constant 1Mbps upstream, if using a remote hosted server you will only ever require just one 128Kbps stream to the server.

The only possible advantage of running icecast yourself that I can think of may be to avoid the cost of renting a shoutcast / icecast server from a provider. I've no idea what caster.fm's business model is that they can offer free icecast services - probably advertising driven at a guess.

I've not had a chance to try setting up icecast locally yet.

---

### Post by eldafani on 2012-03-06
cryptotheslow - Thank you very much, I was missing this very important piece of information. And I will be checking this thread in case you have the time to install icecast2 locally and provide feedback. Also thanks for your help acimi66.

---

### Post by StephenF on 2012-03-07
The login is probably meant to be 'source'.

---

### Post by acimi66 on 2012-03-09
And is mount suppose to be "/stream"?

I am now running into the problem of IDJC and Jack when running/streaming has been crashing my web browser (i use FF but I also tried chrome, and three other free browsers and they ALL crashed) when i go to the site i am broadcasting to... which uses a flash player. I have removed and re-installed the flash plug-in and I still have luck getting it work.

Has anyone else come across this bug?

---

### Post by eldafani on 2012-03-13
It works now. I reinstalled icecast2 including config file and used this configuration in IDJC:

host: <my IP address>
Port: 8000
Mount: /stream
Login: source
Pass: hackme

The stream is located in http://<my IP address>:8000/stream
But only those using my same internet connection can access, that is probably the whole idea of streaming locally. I wanted to stream on a URL that everybody could access, so I will use the remote server I register to in caster.fm. Many thanks anyway.

---

