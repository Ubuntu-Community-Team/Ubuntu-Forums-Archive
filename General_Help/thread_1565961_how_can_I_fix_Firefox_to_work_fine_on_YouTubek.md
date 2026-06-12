---
title: "how can I fix Firefox to work fine on YouTube?k"
date: 2010-09-01
forum: General Help
---

### Post by ieBrazil on 2010-09-01
Hi u there.

You you, my Lucid Lynx is almost 100% good. It just is not working properly on YouTube videos. It can't be stopped or anything... I dont know.

My system is supposed to be updated.

Is it only on my machine? I've gotten a HP Pavilion dv4, 10.04.1 release.

Tnx for any help!


ieBrazil

---

### Post by wojox on 2010-09-01
Check out you neighbor lovinglinux's site 

[Firefox Tutorials]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

---

### Post by lovinglinux on 2010-09-01
> **ieBrazil said:**
> Is it only on my machine? 

That is a common problem that occurs on 64bit systems using the 32bit flash plugin. The solution is listed in the [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html) page.

> **wojox said:**
> Check out you neighbor lovinglinux's site 

[Firefox Tutorials]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

;)

---

### Post by ieBrazil on 2010-09-01
Ih damn!

Now it is being even worse than before!

My browser is cracking just like Windows all: all the time!

Something wrong on installation went wrong probably. Sux :-)





Hey hey! Lovinglinux... I've just visited your blog... nice to meet you here :)

i'll check it out and then, i hope, will mark as SOLVED this thread. Thanks in advance.


iebrazil



> **lovinglinux said:**
> That is a common problem that occurs on 64bit systems using the 32bit flash plugin. The solution is listed in the [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html) page.

ey hey

;)

---

### Post by lovinglinux on 2010-09-01
> **ieBrazil said:**
> Ih damn!

Now it is being even worse than before!

My browser is cracking just like Windows all: all the time!

Something wrong on installation went wrong probably. Sux :-)

Hey hey! Lovinglinux... I've just visited your blog... nice to meet you here :)

i'll check it out and then, i hope, will mark as SOLVED this thread. Thanks in advance.


iebrazil

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by ieBrazil on 2010-09-03
Hi loving...

You see, I knwo what made things go wrong: the line which was supposed to be BEFORE the last one, as asked in the commands you've directed me, I put (pasted) it at the end, instead. 

And when, after a while, when I realized the stupidity I had done, I tried to do it the correct way. And I did indeed. But it did not work well anymore. It kept, you noe, cracking (stoping the system)...

Hope you understand my English. If you want to correct it (my English) too, I'd also thank you :) then I'd learn how to be clearer in this context.

Bye!

I was thinking to myself: is not there a way of deleting ("undoing", if this verb exists) the mal-installed thing and, after, reinstall it the right way?

Thank you ...


ieBrazil


PS: I did not do what you've asked in your previous post because I simply am not using right now my computer. It's at home and I'm at work. (Technically.)

---

### Post by lovinglinux on 2010-09-03
> **ieBrazil said:**
> Hi loving...

You see, I knwo what made things go wrong: the line which was supposed to be BEFORE the last one, as asked in the commands you've directed me, I put (pasted) it at the end, instead. 

And when, after a while, when I realized the stupidity I had done, I tried to do it the correct way. And I did indeed. But it did not work well anymore. It kept, you noe, cracking (stoping the system)...

Hope you understand my English. If you want to correct it (my English) too, I'd also thank you :) then I'd learn how to be clearer in this context.

Bye!

I was thinking to myself: is not there a way of deleting ("undoing", if this verb exists) the mal-installed thing and, after, reinstall it the right way?

Thank you ...


ieBrazil


PS: I did not do what you've asked in your previous post because I simply am not using right now my computer. It's at home and I'm at work. (Technically.)

Run the following commands:

```
sudo apt-get purge lightspark
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge nspluginwrapper
rm -f /home/**/.mozilla/plugins/*flash*so
rm -rf /home/**/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

These commands will reset the flash installation to the state before you applied that fix and will also remove any potential conflicting plugin.

---

### Post by ieBrazil on 2010-09-06
Okay, Loving... I did it and got this:
________________________
isaque@isaque-laptop:~$ sudo apt-get purge lightspark
[sudo] password for isaque: 
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
E: Impossível achar pacote lightspark
isaque@isaque-laptop:~$ sudo apt-get purge swfdec-mozilla
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
O pacote swfdec-mozilla não está instalado, então não será removido
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
isaque@isaque-laptop:~$ sudo apt-get purge mozilla-plugin-gnash
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
O pacote mozilla-plugin-gnash não está instalado, então não será removido
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
isaque@isaque-laptop:~$ sudo apt-get purge nspluginwrapper
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os pacotes a seguir serão REMOVIDOS:
  flashplugin-installer* nspluginwrapper*
0 pacotes atualizados, 0 pacotes novos instalados, 2 a serem removidos e 0 não atualizados.
Depois desta operação, 754kB de espaço em disco serão liberados.
Você quer continuar [S/n]? rm -f /home/**/.mozilla/plugins/*flash*so
Abortar.
isaque@isaque-laptop:~$ S
S: comando não encontrado
isaque@isaque-laptop:~$ rm -f /home/**/.mozilla/plugins/*flash*so
isaque@isaque-laptop:~$ rm -rf /home/**/.wine/dosdevices/c:/windows/system32/Macromed/Flash
isaque@isaque-laptop:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
isaque@isaque-laptop:~$ sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
isaque@isaque-laptop:~$ sudo apt-get install flashplugin-nonfree
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os NOVOS pacotes a seguir serão instalados:
  flashplugin-nonfree
0 pacotes atualizados, 1 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso baixar 2118B de arquivos.
Depois desta operação, 45,1kB adicionais de espaço em disco serão usados.
Obter:1 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse flashplugin-nonfree 10.1.82.76ubuntu0.10.04.2 [2118B]
Baixados 2118B em 1s (1265B/s)              
Selecionando pacote previamente não selecionado flashplugin-nonfree.
(Lendo banco de dados ... 132548 arquivos e diretórios atualmente instalados).
Desempacotando flashplugin-nonfree (de .../flashplugin-nonfree_10.1.82.76ubuntu0.10.04.2_amd64.deb) ...
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.soConfigurando flashplugin-nonfree (10.1.82.76ubuntu0.10.04.2) ...
isaque@isaque-laptop:~$ 
_______________________________________


What do I do now: reinstall it all?

Tnx.



> **lovinglinux said:**
> Run the following commands:

```
sudo apt-get purge lightspark
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge nspluginwrapper
rm -f /home/**/.mozilla/plugins/*flash*so
rm -rf /home/**/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

These commands will reset the flash installation to the state before you applied that fix and will also remove any potential conflicting plugin.

---

### Post by lovinglinux on 2010-09-06
> **ieBrazil said:**
> What do I do now: reinstall it all?

Tnx.

No, you have already done that. Restart Firefox and test it.

---

### Post by ieBrazil on 2010-09-08
> **lovinglinux said:**
> No, you have already done that. Restart Firefox and test it.

Hi.

In fact, my system has returned to the starting point: on YouTube, a message appears on the screen: "It is necessary to update your Adobe F.Player to watch this video; download it from the Adobe site"...

Anyway, at least it is not cracking all the time.

Should I try that command you sent me above again, but now correctly?

---

### Post by lovinglinux on 2010-09-08
> **ieBrazil said:**
> Hi.

In fact, my system has returned to the starting point: on YouTube, a message appears on the screen: "It is necessary to update your Adobe F.Player to watch this video; download it from the Adobe site"...

Anyway, at least it is not cracking all the time.

Should I try that command you sent me above again, but now correctly?


Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/). It will make the process of installing and removing flash easier for you.

---

### Post by ieBrazil on 2010-09-10
Hi you there!

You know, I'll mark this thread as solved, but in fact it is partially solveed: my browser Firefox (3.6.9) only works well (I'm talking about YouTube videos) on videos from English countries... but not from the YouTube Brazil/Portuguese language.

Weird, is not it? It just don't play anything on Brazilians videos on our version of the website, but the USA videos, for example, they work fine.

At least I'll practice my listening more then I've been doing lately, then :)

Bye and thanks you all and thanks, Lovinglinux. Obrigado pela ajuda. Valeu mesmo.


ieBrazil

---

### Post by lovinglinux on 2010-09-11
> **ieBrazil said:**
> Hi you there!

You know, I'll mark this thread as solved, but in fact it is partially solveed: my browser Firefox (3.6.9) only works well (I'm talking about YouTube videos) on videos from English countries... but not from the YouTube Brazil/Portuguese language.

Weird, is not it? It just don't play anything on Brazilians videos on our version of the website, but the USA videos, for example, they work fine.

At least I'll practice my listening more then I've been doing lately, then :)

Bye and thanks you all and thanks, Lovinglinux. Obrigado pela ajuda. Valeu mesmo.


ieBrazil

Looks like a network issue.

---

