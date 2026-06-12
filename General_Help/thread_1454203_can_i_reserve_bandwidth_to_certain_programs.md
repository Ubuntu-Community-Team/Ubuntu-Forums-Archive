---
title: "can i reserve bandwidth to certain programs?"
date: 2010-04-14
forum: General Help
---

### Post by rahilm on 2010-04-14
I have a relatively slow Internet connection. I get around 55 kb/s speeds. When i am updating, which usually takes an hour or mostly two hours, i cannot do anything on the internet. Firefox loads webpages slowly. Apparently, update uses all the 55 kb/s to download. So my question is can i restrict certain programs on internet usage? A kind of speed limit.. I am willing to wait 2-3 hours for the update to finish rather than waiting an hour doing nothing.

---

### Post by dino99 on 2010-04-14
when you says: very slow, do you mean your provider link is bad ? or is it due to your hardware ? how are you connected ?

if your provider is not performant, try other dns like opendns and make change into /etc/hosts

if you cant have better services, well its your own time organization that can be better: i.e. maybe testing is not ideal for you, download when you have nothing else to do with your system.

---

### Post by SevenMachines on 2010-04-14
i think trickle and iprelay in the repositories do this sort of thing, there may be others in there too

---

### Post by rahilm on 2010-04-14
> **dino99 said:**
> when you says: very slow, do you mean your provider link is bad ? or is it due to your hardware ? how are you connected ?

if your provider is not performant, try other dns like opendns and make change into /etc/hosts

if you cant have better services, well its your own time organization that can be better: i.e. maybe testing is not ideal for you, download when you have nothing else to do with your system.

i'll try to look more into this.

> **SevenMachines said:**
> i think trickle and iprelay in the repositories do this sort of thing, there may be others in there too

will try. do you know how to make them work?

---

### Post by SevenMachines on 2010-04-14
> **rahilm said:**
> will try. do you know how to make them work?
sorry, no. i used trickle a few years back looking at the manpages and documentation in /usr/share/doc/<package> (probably). don't think it was too tricky but i really cant remember. there may be some tutorial/howtos out there, i dont know

---

### Post by alfplayer on 2010-04-14
Do you know this trick: [http://www.associatedcontent.com/article/2717695/ubuntu_limiting_download_speed_in_synaptic.html]("http://www.associatedcontent.com/article/2717695/ubuntu_limiting_download_speed_in_synaptic.html") ?

---

### Post by rahilm on 2010-04-15
> **alfplayer said:**
> Do you know this trick: [http://www.associatedcontent.com/article/2717695/ubuntu_limiting_download_speed_in_synaptic.html](http://www.associatedcontent.com/article/2717695/ubuntu_limiting_download_speed_in_synaptic.html) ?
thanks. i will definitely try it when i get my hard drive back.. and when i update again..
does this work only for apt-get?

---

### Post by alfplayer on 2010-04-15
> **rahilm said:**
> thanks. i will definitely try it when i get my hard drive back.. and when i update again..
does this work only for apt-get?

"... is available whether you use Synaptic, the update manager, or apt-get (aptitude) through the command line interface."

---

### Post by rahilm on 2010-04-19
thnx.. it works.. it seems my question is partially solved..

---

### Post by nothingspecial on 2010-04-19
When downloading large files use wget and limit the speed
```

wget --limit-rate=10k http://somewebsite.org/somebigfile.ext
```

It`s pretty self explanitory, that will limit the download sppeed to 20 kb/s, choose what ever number you like.

If you find you need your full bandwith for something else, stop wget, then restart it later on with the -c option

```
wget -c --limit-rate=10k http://somewebsite.org/somebigfile.ext
```

There are loads of options

```
man wget
```

---

### Post by rahilm on 2010-04-19
> **nothingspecial said:**
> When downloading large files use wget and limit the speed
```

wget --limit-rate=10k [http://somewebsite.org/somebigfile.ext](http://somewebsite.org/somebigfile.ext)
```It`s pretty self explanitory, that will limit the download sppeed to 20 kb/s, choose what ever number you like.

If you find you need your full bandwith for something else, stop wget, then restart it later on with the -c option

```
wget -c --limit-rate=10k [http://somewebsite.org/somebigfile.ext](http://somewebsite.org/somebigfile.ext)
```There are loads of options

```
man wget
```

thanks, i can control pretty much everything now..
apt-get can be limited
wget can be limited
deluge can be limited

although i am still looking for an independant GUI to control universal speed allowance.

SOLVED

---

