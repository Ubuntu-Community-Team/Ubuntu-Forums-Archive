---
title: "watching live stream in media player"
date: 2010-12-19
forum: General Help
---

### Post by krishna1650 on 2010-12-19
Hello all,
Can anyone provide details how to watch live streams in media player (like in totem, vlc, mplayer or any other available in ubuntu). I have tried lot, but couldn't find any solution.  

Thanks

---

### Post by krishna1650 on 2010-12-19
Please at-least give some hint, how to start.

---

### Post by amsterdamharu on 2010-12-19
Ubuntu comes with a certain amount of codecs that are open source, not  sure if Windows media fits into that. For example mpeg is closed source,  that means that someone has a patent on it and anyone making software  using those codecs has to have permission from the patent holder. This  can be given for money or just like that, the biggest problem is that  the person using the codec for his/her software never owns the codec so  cannot re write it to fix something or can have the patent holder change  conditions whenever they please.
It can even go so far that the the patent holder suing the software  producer or the software user (you) for using their patented piece of  software code.
Luckily these software patents are only in the US and Japan so if you're outside you can install the codecs like this.

Copy and paste the following in the terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  && sudo apt-get --quiet update && sudo apt-get --yes  --quiet --allow-unauthenticated install medibuntu-keyring &&  sudo apt-get --quiet update
sudo apt-get install non-free-codecs vlc mozilla-plugin-vlc
```Now open vlc (press control + f2 and type vlc or find it in your application menu) -> tools messages -> set verbosity level to 2 -> alt tab to vlc -> media -> open network stream

If anything goes wrong can you please post the messages in the messages window?

---

### Post by Vigh on 2010-12-19
install ubuntu restricted extras for mp3 etc. support through software centre, when you want to stream something whether it be a radio station or whatever, instead of clicking on the link, right click copy link location and then click open network stream in VLC, paste and click play, VLC seems to have the smoothest playback for streams imo whilst also being able to seek through a stream, hope this helps

---

### Post by amsterdamharu on 2010-12-19
@Vigh
Do you know the difference between restricted extras and medibuntu? I am confused why help.ubuntu.com tells you to do one thing or the other depending what page you open.

I just said:
> Mint doesn't have the ubuntu-restricted-extras installed after I installed the non-free-codecs but needed the non-free-codecs to be able to encode in avi or mpeg with ffmpeg.
See now that according to synaptic neither is installed on my mint 9 but I have no problem playing and encoding restricted formats so not sure how mint does it.

---

### Post by krishna1650 on 2010-12-19
> **amsterdamharu said:**
> Ubuntu comes with a certain amount of codecs that are open source, not  sure if Windows media fits into that. For example mpeg is closed source,  that means that someone has a patent on it and anyone making software  using those codecs has to have permission from the patent holder. This  can be given for money or just like that, the biggest problem is that  the person using the codec for his/her software never owns the codec so  cannot re write it to fix something or can have the patent holder change  conditions whenever they please.
It can even go so far that the the patent holder suing the software  producer or the software user (you) for using their patented piece of  software code.
Luckily these software patents are only in the US and Japan so if you're outside you can install the codecs like this.

Copy and paste the following in the terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  && sudo apt-get --quiet update && sudo apt-get --yes  --quiet --allow-unauthenticated install medibuntu-keyring &&  sudo apt-get --quiet update
sudo apt-get install non-free-codecs vlc mozilla-plugin-vlc
```Now open vlc (press control + f2 and type vlc or find it in your application menu) -> tools messages -> set verbosity level to 2 -> alt tab to vlc -> media -> open network stream

If anything goes wrong can you please post the messages in the messages window?

Thanks for reply. I tried to watch "times now" tv online (indian news tv channel) using vlc. The link is [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1) and the log is given below. Please mention the errors and how to correct them. Thanks again for reply.


qt4 warning: Input option: http-caching=1200
main debug: adding item `[http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1)' ( [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1) )
qt4 debug: Adding a new MRL to recent ones: [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1)
main debug: rebuilding array of current - root Playlist
main debug: rebuild done - 2 items, index 0
main debug: processing request item [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1) node null skip 0
main debug: resyncing on [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1)
main debug: [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1) is at 1
main debug: starting new item
main debug: creating new input thread
main debug: Creating an input for 'http://live.indiatimes.com/default.cms?timesnow=1'
main debug: thread (input) created at priority 10 (input/input.c:214)
main debug: TIMER input launching for 'http://live.indiatimes.com/default.cms?timesnow=1' : 19980.223 ms - Total 19980.223 ms / 1 intvls (Avg 19980.222 ms)
main debug: meta ok for (null), need to fetch art
main debug: thread started
main debug: using timeshift granularity of 50 MiB
main debug: using timeshift path '/tmp'
main debug: `[http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1)' gives access `http' demux `' path `live.indiatimes.com/default.cms?timesnow=1'
main debug: creating demux: access='http' demux='' path='live.indiatimes.com/default.cms?timesnow=1'
main debug: looking for access_demux module: 0 candidates
main debug: no access_demux module matched "http"
main debug: TIMER module_need() : 0.361 ms - Total 0.361 ms / 1 intvls (Avg 0.361 ms)
main debug: creating access 'http' path='live.indiatimes.com/default.cms?timesnow=1'
main debug: looking for access module: 2 candidates
qt4 debug: IM: Setting an input
access_http debug: asking libproxy about url 'http://live.indiatimes.com/default.cms?timesnow=1'
access_http debug: libproxy suggest to use 'http://netmon.iitb.ac.in:80'
access_http debug: http: server='live.indiatimes.com' port=80 file='/default.cms?timesnow=1'
access_http debug:       proxy netmon.iitb.ac.in:80
main debug: net: connecting to netmon.iitb.ac.in port 80
main debug: connection succeeded (socket = 24)
access_http debug: protocol 'HTTP' answer code 407
access_http error: error: HTTP/1.0 407 Proxy Authentication Required
access_http debug: switching to HTTP version 1.0
main debug: net: connecting to netmon.iitb.ac.in port 80
main debug: connection succeeded (socket = 24)
access_http debug: protocol 'HTTP' answer code 407
access_http error: error: HTTP/1.0 407 Proxy Authentication Required
access_mms debug: Using http proxy netmon.iitb.ac.in:80
main debug: net: connecting to netmon.iitb.ac.in port 80
main debug: connection succeeded (socket = 24)
access_mms error: error: HTTP/1.0 407 Proxy Authentication Required
main debug: no access module matching "http" could be loaded
main debug: TIMER module_need() : 291.431 ms - Total 291.431 ms / 1 intvls (Avg 291.431 ms)
main debug: waitpipe: object killed
main error: open of `[http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1)' failed: (null)
main debug: thread ended
main debug: dead input
main debug: changing item without a request (current 1/2)
main debug: nothing to play
main debug: looking for meta fetcher module: 1 candidate
lua debug: Trying Lua scripts in /home/krishna/.local/share/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
qt4 debug: IM: Deleting the input
main debug: using meta fetcher module "lua"
main debug: TIMER module_need() : 46.250 ms - Total 46.250 ms / 1 intvls (Avg 46.250 ms)
main debug: removing module "lua"
main debug: searching art for [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1)
main debug: looking for art finder module: 2 candidates
lua debug: Trying Lua scripts in /home/krishna/.local/share/vlc/lua/meta/art
lua debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/04_musicbrainz.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
main debug: no art finder module matching "any" could be loaded
main debug: TIMER module_need() : 37.642 ms - Total 37.642 ms / 1 intvls (Avg 37.642 ms)
main debug: art not found for [http://live.indiatimes.com/default.cms?timesnow=1](http://live.indiatimes.com/default.cms?timesnow=1)

---

### Post by amsterdamharu on 2010-12-19
That link is not a mms stream, it's a http protocol that returns a web page containing a flash player that opens some video or sound.

I suggest opening that link in firefox.

You also use a proxy, I guess you're at work or school? The proxy requires authentication according to the log. Does this sound familiar: Using http proxy netmon.iitb.ac.in:80?

---

### Post by krishna1650 on 2010-12-20
Thanks for reply.

So there is no way to play this kind of link (http page showing some live videos) ?

---

### Post by amsterdamharu on 2010-12-20
mms is a protocol like mms://somelocation.somestream http is a protocol like [http://google.com](http://google.com).
Http usually returns a html page (what you are watching right now in firefox), not a movie. The page can have a movie on it, usually with flash.

As i've said before try opening that link in your browser.

If it still doesn't work try installing the flash plugin by copying the following command:
```
sudo apt-get install adobe-flashplugin
```

---

### Post by krishna1650 on 2010-12-30
> **amsterdamharu said:**
> That link is not a mms stream, it's a http protocol that returns a web page containing a flash player that opens some video or sound.

I suggest opening that link in firefox.

You also use a proxy, I guess you're at work or school? The proxy requires authentication according to the log. Does this sound familiar: Using http proxy netmon.iitb.ac.in:80?
Can you please tell, how to add proxy settings in vlc (in ubuntu)?

thanks

---

### Post by amsterdamharu on 2010-12-30
Press alt + F2, type gnome-control-center and click run. In the filter type proxy and yo should be left with network proxy.

---

