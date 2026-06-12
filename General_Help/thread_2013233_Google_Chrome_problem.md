---
title: "Google Chrome problem"
date: 2012-06-30
forum: General Help
---

### Post by Chelidze on 2012-06-30
I do not know if this is the right place to write about google chrome or not so sorry if it is not 
 after the update ,,Google Chrome 20.0.1132.47" google chrome started to lag ,,It gets stuck for couple of seconds and then it resumes" i think it starts lagging when i enter any flash site 

 when i started chrome from the terminal it showed this before the update non of this appeared 

```
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_direct.c:980:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dsnoop.c:623:(snd_pcm_dsnoop_open) unable to initialize slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_direct.c:980:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dsnoop.c:623:(snd_pcm_dsnoop_open) unable to initialize slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_direct.c:980:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dsnoop.c:623:(snd_pcm_dsnoop_open) unable to initialize slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_direct.c:980:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dsnoop.c:623:(snd_pcm_dsnoop_open) unable to initialize slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_direct.c:980:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dsnoop.c:623:(snd_pcm_dsnoop_open) unable to initialize slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_direct.c:980:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dsnoop.c:623:(snd_pcm_dsnoop_open) unable to initialize slave

```

is there a way to fix this and thank you for your time

---

### Post by vasa1 on 2012-06-30
See [http://askubuntu.com/questions/158009/google-chrome-freezes-for-seconds](http://askubuntu.com/questions/158009/google-chrome-freezes-for-seconds) ;)

---

### Post by Chelidze on 2012-06-30
> **vasa1 said:**
> See [http://askubuntu.com/questions/158009/google-chrome-freezes-for-seconds](http://askubuntu.com/questions/158009/google-chrome-freezes-for-seconds) ;)

thanks hope they will fix this soon

---

### Post by jasonsmith01 on 2012-06-30
Ya noticed that with the last two updates of Chrome. Chromium is working perfect thankfully.

Using the following fixes it as suggested in askubuntu.
```
google-chrome --disable-bundled-ppapi-flash
```

---

### Post by Chelidze on 2012-06-30
Using the following fixes it as suggested in askubuntu.
```
google-chrome --disable-bundled-ppapi-flash
```[/QUOTE]

thank you 
it works now

---

### Post by tristan8276 on 2012-06-30
I'm still having trouble displaying flash videos in my browser after the new update.  I can launch chrome now using the above solution.  Thank you for sharing that :)  Can anyone verify that flash is still not working properly?  I can't seem to get any good logs of the problem, but I will post them when I do.

Please understand that I am only seeking any advice on this issue.  I know that this is a development community and I also am aware that my computer is very outdated and I'm lucky it runs at all.  I mean no disrespect to the Ubuntu community.  I also know that I shouldn't just ask for answers to be given and that I should learn for myself.  I just wanted to see if anyone had any ideas.

---

### Post by lovinglinux on 2012-06-30
> **tristan8276 said:**
> I'm still having trouble displaying flash videos in my browser after the new update.  I can launch chrome now using the above solution.  Thank you for sharing that :)  Can anyone verify that flash is still not working properly?  I can't seem to get any good logs of the problem, but I will post them when I do.

Please understand that I am only seeking any advice on this issue.  I know that this is a development community and I also am aware that my computer is very outdated and I'm lucky it runs at all.  I mean no disrespect to the Ubuntu community.  I also know that I shouldn't just ask for answers to be given and that I should learn for myself.  I just wanted to see if anyone had any ideas.

I am not experiencing any issues with the new PepperFlash.

I am not sure if this is the case, but my plugins are set to play on click in "Privacy >> Content Settings". You could try that.

---

### Post by vasa1 on 2012-06-30
> **lovinglinux said:**
> I am not experiencing any issues with the new PepperFlash.

I am not sure if this is the case, but my plugins are set to play on click in "Privacy >> Content Settings". You could try that.

I can't try that since I too do not have the problem. People can follow developments here:
[http://code.google.com/p/chromium/issues/detail?id=134940](http://code.google.com/p/chromium/issues/detail?id=134940)
and
[http://productforums.google.com/forum/#!category-topic/chrome/linux/UVGRyv50t0E](http://productforums.google.com/forum/#!category-topic/chrome/linux/UVGRyv50t0E)

@Lovinglinux, if you have a Google account, you could suggest trying "click to play" in both sites?

The bad news, for those who face the problem, is that the bug is still "available" implying that no one has agreed to work on it. (The base of Linux users of Chrome is pretty small making troubleshooting data hard to come by.)

---

### Post by lovinglinux on 2012-07-01
> **vasa1 said:**
> I can't try that since I too do not have the problem. People can follow developments here:
[http://code.google.com/p/chromium/issues/detail?id=134940](http://code.google.com/p/chromium/issues/detail?id=134940)
and
[http://productforums.google.com/forum/#!category-topic/chrome/linux/UVGRyv50t0E](http://productforums.google.com/forum/#!category-topic/chrome/linux/UVGRyv50t0E)

@Lovinglinux, if you have a Google account, you could suggest trying "click to play" in both sites?

The bad news, for those who face the problem, is that the bug is still "available" implying that no one has agreed to work on it. (The base of Linux users of Chrome is pretty small making troubleshooting data hard to come by.)

Let's see if this solves the problem first. Need feedback from those experiencing this issue.

---

### Post by vasa1 on 2012-07-01
> **lovinglinux said:**
> Let's see if this solves the problem first. Need feedback from those experiencing this issue.
You may get a wider audience at the Google forums. There, people with other distros are also posting.

---

### Post by tristan8276 on 2012-07-02
I have to run Chrome from terminal with 'google-chrome --disable-bundled-ppapi-flash' otherwise it doesn't do anything when I try to load it.  Here's the output in the terminal when I run Chrome with 'google-chrome --disable-bundled-ppapi-flash' and try to test my flash plugin:


[15:15:1075263110:ERROR:webplugin_delegate_proxy.cc(353)] PluginMsg_Init returned false
[15:15:1075306216:ERROR:webplugin_impl.cc(269)] Couldn't initialize plug-in
--2012-07-02 09:07:12--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... 74.125.239.3, 74.125.239.4, 74.125.239.5, ...
Connecting to clients2.google.com|74.125.239.3|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [ <=>                                   ] 16          --.-K/s   in 0s      

2012-07-02 09:07:12 (149 KB/s) - `/dev/fd/3' saved [16]


Crash dump id: 6bdd80b79a83e0eb
[15:15:1076732067:ERROR:webplugin_delegate_proxy.cc(353)] PluginMsg_Init returned false
[15:15:1076732186:ERROR:webplugin_impl.cc(269)] Couldn't initialize plug-in
[15:15:1076741016:ERROR:webplugin_delegate_proxy.cc(292)] Plug-in crashed on start
--2012-07-02 09:07:13--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... 74.125.224.227, 74.125.224.228, 74.125.224.229, ...
Connecting to clients2.google.com|74.125.224.227|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                    ] 0           --.-K/s              
Crash dump id: a091f52fe7f887eb

[15:15:1151810830:ERROR:webplugin_delegate_proxy.cc(353)] PluginMsg_Init returned false
[15:15:1151810955:ERROR:webplugin_impl.cc(269)] Couldn't initialize plug-in
--2012-07-02 09:08:28--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... 74.125.224.160, 74.125.224.161, 74.125.224.162, ...
Connecting to clients2.google.com|74.125.224.160|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                    ] 0           --.-K/s              
Crash dump id: f9c93666a88fa457
[15:15:1152854180:ERROR:webplugin_delegate_proxy.cc(353)] PluginMsg_Init returned false
[15:15:1152854298:ERROR:webplugin_impl.cc(269)] Couldn't initialize plug-in
[15:15:1152882078:ERROR:webplugin_delegate_proxy.cc(292)] Plug-in crashed on start
--2012-07-02 09:08:29--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... 74.125.224.229, 74.125.224.230, 74.125.224.231, ...
Connecting to clients2.google.com|74.125.224.229|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                    ] 0           --.-K/s              
Crash dump id: 51932c722f0b371f

---

### Post by jasonsmith01 on 2012-07-05
```
google-chrome --disable-bundled-ppapi-flash
``` 

^^ Still corrects all my lagging issues. Now, how to actually fix this so I don't have to start it in terminal all the time. Sadly I've almost stopped caring as Chromium is working great.

EDIT: All flash websites and tests work fine after I start it this way. I don't get the errors in the above post.

---

