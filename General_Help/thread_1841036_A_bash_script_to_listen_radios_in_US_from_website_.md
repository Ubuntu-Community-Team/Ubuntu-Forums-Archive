---
title: "A bash script to listen radios in US from website page?"
date: 2011-09-08
forum: General Help
---

### Post by honeybear on 2011-09-08
Hello,

Little bit like shoutcast, it could be great that a bash script could prompt you the radios in a dialog (console) menu, and play the selected one with mplayer

It could be a great idea of code.

Here please find the list of a great number of radios, for input data to wget : 
[http://www.usliveradio.com/](http://www.usliveradio.com/)

Happy Tux !
Thank you, for this open shoutcast like thing

---

### Post by andrew.46 on 2011-09-08
Not a bash script but the '[Streaming Radio Player extension for VLC]("http://www.coderholic.com/extending-vlc-with-lua/")' by Ben Dowling might be useful to you...

---

### Post by honeybear on 2011-09-09
> **andrew.46 said:**
> Not a bash script but the '[Streaming Radio Player extension for VLC]("http://www.coderholic.com/extending-vlc-with-lua/")' by Ben Dowling might be useful to you...

Pretty cool indeed. thankx

However would you know an alternative if this one to bash? Is there a downlooadable list of this plugin on the web? 

Sounds cool. I wget this link URL of VLC; and make it a  bash script

H E L P

---

### Post by HermanAB on 2011-09-09
My favourite is streamtuner.

---

### Post by nothingspecial on 2011-09-09
I use aliases. I have a number of favourite radio stations for different genres. So in my .bash_aliases file I have certain entries. For example

```
alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'
```

Don't worry, the -really-quiet option jsut suppresses all mplayer's output, you can still have it loud :P

So, all I have to do to listen to some punk is type

```
punk
```

I also have ones for blues, jazz, classical, metal etc etc and most of the bbc stations.

It's the same line every time

```
alias [COLOR="Red"]genre[/COLOR]='mplayer -really-quiet [COLOR="Red"]address[/COLOR] < /dev/null &'
```

But I'm sure you could config it how you like.

```
punk
```
:twisted:

---

### Post by honeybear on 2011-09-09
> **HermanAB said:**
> My favourite is streamtuner.

Could you post please the file that contains all the streams from ~/.streamtuner, please? Then I can try to convert it to an useable list of stream, for a cool bash script ;)

---

### Post by honeybear on 2011-09-09
> **nothingspecial said:**
> I use aliases. I have a number of favourite radio stations for different genres. So in my .bash_aliases file I have certain entries. For example

```
alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'
```

Don't worry, the -really-quiet option jsut suppresses all mplayer's output, you can still have it loud :P

So, all I have to do to listen to some punk is type

```
punk
```

I also have ones for blues, jazz, classical, metal etc etc and most of the bbc stations.

It's the same line every time

```
alias [COLOR="Red"]genre[/COLOR]='mplayer -really-quiet [COLOR="Red"]address[/COLOR] < /dev/null &'
```

But I'm sure you could config it how you like.

```
punk
```
:twisted:

Thanks. Your IP adress is one of punk stream. Cool punk music thx. I am sure we coudl convert vlc or streamtuner for making an online streamer using console
```
ICY 200 OK
icy-notice1:<BR>This stream requires <a href="http://www.winamp.com/">Winamp</a><BR>
icy-notice2:SHOUTcast Distributed Network Audio Server/Linux v1.9.7<BR>
icy-name:Horns Up! Metal Radio
icy-genre:death metal, metal hardcore,
icy-url:www.hornsupmetal.com
content-type:audio/mpeg
icy-pub:1
icy-br:128

```

---

### Post by andrew.46 on 2011-09-09
> **nothingspecial said:**
> I use aliases. I have a number of favourite radio stations for different genres.

Great idea which I am now using :).

---

### Post by honeybear on 2011-09-10
> **andrew.46 said:**
> Great idea which I am now using :).

why not dialog, xdialog, or zenity, from a list?

---

