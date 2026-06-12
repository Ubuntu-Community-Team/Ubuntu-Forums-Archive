---
title: "Please suggest me command to execute .."
date: 2011-11-01
forum: General Help
---

### Post by rushikesh988 on 2011-11-01
hello friends I want to install the following packages in my system.

[COLOR="Black"][B]perl-devel, 
SDL-devel,
 SDL_image-devel, 
SDL_mixer-devel 
freetype2-devel
[/B][/COLOR]

please give me a commands to execute in terminal :confused:


..is there any way to execute list of commands at a time??:confused:

---

### Post by oldos2er on 2011-11-01
Use apt-cache search to find the correct package names. *apt-get install* can handle as many packages as you need (I've never come across a limit).

Use && or ; to string together commands, e.g. ```
sudo apt-get update && sudo apt-get upgrade
``` ```
cd /etc/apt/sources.list.d/ ; sudo nano sources.list
```

---

### Post by rushikesh988 on 2011-11-01
brother I got this replies from terminal please suggest me how to find a name with example 
"> rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 154 not upgraded.
rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo apt-cache perl-devel
E: Invalid operation perl-devel
rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo apt-cache showpkg perl-devel
N: Unable to locate package perl-devel
rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo apt-cache gencaches perl-devel
Reading package lists... Done

I was unable to find name that I can use with
> sudo apt-get install
I also tried with the name only and got this reply
> rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo apt-get install perl-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package perl-devel
rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ 


---

### Post by gandaran on 2011-11-01
> **rushikesh988 said:**
> hello friends I want to install the following packages in my system.

[COLOR="Black"][B]perl-devel, 
SDL-devel,
 SDL_image-devel, 
SDL_mixer-devel 
freetype2-devel
[/B][/COLOR]

please give me a commands to execute in terminal :confused:


..is there any way to execute list of commands at a time??:confused:
use synaptic package manager (you don't have it install it) to find the packages and install, those packages most likely begin with 'lib' on ubuntu so 'perl-devel' would be 'libperl-devel'

---

### Post by oldos2er on 2011-11-01
There is no package named perl-devel, which is why I suggested you use apt-cache search. For example ```
apt-cache search perl-dev
libperl-dev - Perl library: development files
``` and repeat the process for the other files you need. You may need to change the search terms a little to help narrow down the results.

---

### Post by rushikesh988 on 2011-11-01
> **gandaran said:**
> use synaptic package manager (you don't have it install it) to find the packages and install, those packages most likely begin with 'lib' on ubuntu so 'perl-devel' would be 'libperl-devel'
bt I have heard that synaptic is removed from 11.10 ??
I was unable to find it ..can u tell me how to start it

---

### Post by rushikesh988 on 2011-11-01
I have installed all the packages bt still I am unable to install this application can you please tell me whats wrong

> rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for working const... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for sdl-config... (cached) /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for IMG_Load in -lSDL_image... (cached) yes
checking for Mix_OpenAudio in -lSDL_mixer... (cached) yes
checking for SDLNet_ResolveHost in -lSDL_net... (cached) yes
checking for freetype-config... (cached) /usr/bin/freetype-config
checking for FreeType - version >= 2.1.0... yes
checking for perl... (cached) /usr/bin/perl
checking for flags to compile embedded Perl...  -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I/usr/lib/perl/5.12/CORE 
creating ./config.status
creating Makefile
creating src/Makefile
creating data/Makefile
creating data/characters/Makefile
creating data/fonts/Makefile
creating data/gfx/Makefile
creating data/script/Makefile
creating data/sound/Makefile
creating config.h
config.h is unchanged


Trying to make makefile
> rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo make
make  all-recursive
make[1]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7'
Making all in data
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
Making all in fonts
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/fonts'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/fonts'
Making all in gfx
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/gfx'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/gfx'
Making all in script
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/script'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/script'
Making all in sound
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/sound'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/sound'
Making all in characters
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/characters'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/characters'
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
Making all in src
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/src'
c++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/freetype2  -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I/usr/lib/perl/5.12/CORE  -DDATADIR=\"/usr/local/share/openmortal\" -Wall -c OnlineChat.cpp
OnlineChat.cpp:59:2: error: extra qualification &#8216;CChallengeMenu::&#8217; on member &#8216;CChallengeMenu&#8217; [-fpermissive]
make[2]: *** [OnlineChat.o] Error 1
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7'
make: *** [all-recursive-am] Error 2
rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ 


Trying to install app with make install
> rushikesh988@rushikesh988-AOD257:~/Desktop/openmortal-0.7$ sudo make install
Making install in data
make[1]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
Making install in fonts
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/fonts'
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/fonts'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/local/share/openmortal/fonts
 /usr/bin/install -c -m 644 ./aardvark.ttf /usr/local/share/openmortal/fonts/aardvark.ttf
 /usr/bin/install -c -m 644 ./bradybun.ttf /usr/local/share/openmortal/fonts/bradybun.ttf
 /usr/bin/install -c -m 644 ./deadgrit.ttf /usr/local/share/openmortal/fonts/deadgrit.ttf
 /usr/bin/install -c -m 644 ./thin.ttf /usr/local/share/openmortal/fonts/thin.ttf
 /usr/bin/install -c -m 644 ./brandybun3.png /usr/local/share/openmortal/fonts/brandybun3.png
 /usr/bin/install -c -m 644 ./glossyfont.png /usr/local/share/openmortal/fonts/glossyfont.png
 /usr/bin/install -c -m 644 ./CreditsFont2.png /usr/local/share/openmortal/fonts/CreditsFont2.png
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/fonts'
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/fonts'
Making install in gfx
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/gfx'
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/gfx'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/local/share/openmortal/gfx
 /usr/bin/install -c -m 644 ./Credits.jpg /usr/local/share/openmortal/gfx/Credits.jpg
 /usr/bin/install -c -m 644 ./level3_ground.png /usr/local/share/openmortal/gfx/level3_ground.png
 /usr/bin/install -c -m 644 ./level7_cumi.png /usr/local/share/openmortal/gfx/level7_cumi.png
 /usr/bin/install -c -m 644 ./Doodads.png /usr/local/share/openmortal/gfx/Doodads.png
 /usr/bin/install -c -m 644 ./level3_moon.png /usr/local/share/openmortal/gfx/level3_moon.png
 /usr/bin/install -c -m 644 ./level7.desc /usr/local/share/openmortal/gfx/level7.desc
 /usr/bin/install -c -m 644 ./FighterStats.jpg /usr/local/share/openmortal/gfx/FighterStats.jpg
 /usr/bin/install -c -m 644 ./level3_sky.png /usr/local/share/openmortal/gfx/level3_sky.png
 /usr/bin/install -c -m 644 ./level7_ground1.png /usr/local/share/openmortal/gfx/level7_ground1.png
 /usr/bin/install -c -m 644 ./Foot.jpg /usr/local/share/openmortal/gfx/Foot.jpg
 /usr/bin/install -c -m 644 ./level4.desc /usr/local/share/openmortal/gfx/level4.desc
 /usr/bin/install -c -m 644 ./level7_ground2.png /usr/local/share/openmortal/gfx/level7_ground2.png
 /usr/bin/install -c -m 644 ./Foot.mask.png /usr/local/share/openmortal/gfx/Foot.mask.png
 /usr/bin/install -c -m 644 ./level4_earth.jpg /usr/local/share/openmortal/gfx/level4_earth.jpg
 /usr/bin/install -c -m 644 ./level7_ground3.png /usr/local/share/openmortal/gfx/level7_ground3.png
 /usr/bin/install -c -m 644 ./GameOver.jpg /usr/local/share/openmortal/gfx/GameOver.jpg
 /usr/bin/install -c -m 644 ./level4_earth.mask.png /usr/local/share/openmortal/gfx/level4_earth.mask.png
 /usr/bin/install -c -m 644 ./level7_ground4.png /usr/local/share/openmortal/gfx/level7_ground4.png
 /usr/bin/install -c -m 644 ./icon.bmp /usr/local/share/openmortal/gfx/icon.bmp
 /usr/bin/install -c -m 644 ./level4_ground.jpg /usr/local/share/openmortal/gfx/level4_ground.jpg
 /usr/bin/install -c -m 644 ./level7_logo.png /usr/local/share/openmortal/gfx/level7_logo.png
 /usr/bin/install -c -m 644 ./icon.png /usr/local/share/openmortal/gfx/icon.png
 /usr/bin/install -c -m 644 ./level4_ground.mask.png /usr/local/share/openmortal/gfx/level4_ground.mask.png
 /usr/bin/install -c -m 644 ./level7_sky.png /usr/local/share/openmortal/gfx/level7_sky.png
 /usr/bin/install -c -m 644 ./level10.desc /usr/local/share/openmortal/gfx/level10.desc
 /usr/bin/install -c -m 644 ./level4_moon.jpg /usr/local/share/openmortal/gfx/level4_moon.jpg
 /usr/bin/install -c -m 644 ./level7_upi.png /usr/local/share/openmortal/gfx/level7_upi.png
 /usr/bin/install -c -m 644 ./level10_ground.png /usr/local/share/openmortal/gfx/level10_ground.png
 /usr/bin/install -c -m 644 ./level4_moon.mask.png /usr/local/share/openmortal/gfx/level4_moon.mask.png
 /usr/bin/install -c -m 644 ./level8.jpg /usr/local/share/openmortal/gfx/level8.jpg
 /usr/bin/install -c -m 644 ./level10_hill.png /usr/local/share/openmortal/gfx/level10_hill.png
 /usr/bin/install -c -m 644 ./level4_nebula.jpg /usr/local/share/openmortal/gfx/level4_nebula.jpg
 /usr/bin/install -c -m 644 ./level9.jpg /usr/local/share/openmortal/gfx/level9.jpg
 /usr/bin/install -c -m 644 ./level10_sky.png /usr/local/share/openmortal/gfx/level10_sky.png
 /usr/bin/install -c -m 644 ./level4_rock.jpg /usr/local/share/openmortal/gfx/level4_rock.jpg
 /usr/bin/install -c -m 644 ./Mortal-en.jpg /usr/local/share/openmortal/gfx/Mortal-en.jpg
 /usr/bin/install -c -m 644 ./level11.jpg /usr/local/share/openmortal/gfx/level11.jpg
 /usr/bin/install -c -m 644 ./level4_rock.mask.png /usr/local/share/openmortal/gfx/level4_rock.mask.png
 /usr/bin/install -c -m 644 ./Mortal.jpg /usr/local/share/openmortal/gfx/Mortal.jpg
 /usr/bin/install -c -m 644 ./level1.jpg /usr/local/share/openmortal/gfx/level1.jpg
 /usr/bin/install -c -m 644 ./level4_saturn.jpg /usr/local/share/openmortal/gfx/level4_saturn.jpg
 /usr/bin/install -c -m 644 ./Story1.jpg /usr/local/share/openmortal/gfx/Story1.jpg
 /usr/bin/install -c -m 644 ./level2.jpg /usr/local/share/openmortal/gfx/level2.jpg
 /usr/bin/install -c -m 644 ./level4_saturn.mask.png /usr/local/share/openmortal/gfx/level4_saturn.mask.png
 /usr/bin/install -c -m 644 ./Story2.jpg /usr/local/share/openmortal/gfx/Story2.jpg
 /usr/bin/install -c -m 644 ./level3_city.png /usr/local/share/openmortal/gfx/level3_city.png
 /usr/bin/install -c -m 644 ./level5.jpg /usr/local/share/openmortal/gfx/level5.jpg
 /usr/bin/install -c -m 644 ./eu.jpg /usr/local/share/openmortal/gfx/eu.jpg
 /usr/bin/install -c -m 644 ./level3.desc /usr/local/share/openmortal/gfx/level3.desc
 /usr/bin/install -c -m 644 ./level6.jpg /usr/local/share/openmortal/gfx/level6.jpg
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/gfx'
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/gfx'
Making install in script
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/script'
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/script'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/local/share/openmortal/script
 /usr/bin/install -c -m 644 ./Backend.pl /usr/local/share/openmortal/script/Backend.pl
 /usr/bin/install -c -m 644 ./Collision.pl /usr/local/share/openmortal/script/Collision.pl
 /usr/bin/install -c -m 644 ./Doodad.pl /usr/local/share/openmortal/script/Doodad.pl
 /usr/bin/install -c -m 644 ./Keys.pl /usr/local/share/openmortal/script/Keys.pl
 /usr/bin/install -c -m 644 ./Rewind.pl /usr/local/share/openmortal/script/Rewind.pl
 /usr/bin/install -c -m 644 ./CollectedStats.pl /usr/local/share/openmortal/script/CollectedStats.pl
 /usr/bin/install -c -m 644 ./Damage.pl /usr/local/share/openmortal/script/Damage.pl
 /usr/bin/install -c -m 644 ./Fighter.pl /usr/local/share/openmortal/script/Fighter.pl
 /usr/bin/install -c -m 644 ./PlayerInput.pl /usr/local/share/openmortal/script/PlayerInput.pl
 /usr/bin/install -c -m 644 ./State.pl /usr/local/share/openmortal/script/State.pl
 /usr/bin/install -c -m 644 ./CollectStats.pl /usr/local/share/openmortal/script/CollectStats.pl
 /usr/bin/install -c -m 644 ./DataHelper.pl /usr/local/share/openmortal/script/DataHelper.pl
 /usr/bin/install -c -m 644 ./FighterStats.pl /usr/local/share/openmortal/script/FighterStats.pl
 /usr/bin/install -c -m 644 ./QuickSave.pl /usr/local/share/openmortal/script/QuickSave.pl
 /usr/bin/install -c -m 644 ./Translate.pl /usr/local/share/openmortal/script/Translate.pl
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/script'
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/script'
Making install in sound
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/sound'
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/sound'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/local/share/openmortal/sound
 /usr/bin/install -c -m 644 ./2nd_pm.s3m /usr/local/share/openmortal/sound/2nd_pm.s3m
 /usr/bin/install -c -m 644 ./beepdoub.wav /usr/local/share/openmortal/sound/beepdoub.wav
 /usr/bin/install -c -m 644 ./cow.wav /usr/local/share/openmortal/sound/cow.wav
 /usr/bin/install -c -m 644 ./evilpsychola.wav /usr/local/share/openmortal/sound/evilpsychola.wav
 /usr/bin/install -c -m 644 ./movemenu.wav /usr/local/share/openmortal/sound/movemenu.wav
 /usr/bin/install -c -m 644 ./splat2.voc /usr/local/share/openmortal/sound/splat2.voc
 /usr/bin/install -c -m 644 ./thump.wav /usr/local/share/openmortal/sound/thump.wav
 /usr/bin/install -c -m 644 ./apert.wav /usr/local/share/openmortal/sound/apert.wav
 /usr/bin/install -c -m 644 ./beepdrop.wav /usr/local/share/openmortal/sound/beepdrop.wav
 /usr/bin/install -c -m 644 ./curve.wav /usr/local/share/openmortal/sound/curve.wav
 /usr/bin/install -c -m 644 ./hit_ground.wav /usr/local/share/openmortal/sound/hit_ground.wav
 /usr/bin/install -c -m 644 ./ride.mod /usr/local/share/openmortal/sound/ride.mod
 /usr/bin/install -c -m 644 ./splat.wav /usr/local/share/openmortal/sound/splat.wav
 /usr/bin/install -c -m 644 ./top.wav /usr/local/share/openmortal/sound/top.wav
 /usr/bin/install -c -m 644 ./aroooga.voc /usr/local/share/openmortal/sound/aroooga.voc
 /usr/bin/install -c -m 644 ./bowling.voc /usr/local/share/openmortal/sound/bowling.voc
 /usr/bin/install -c -m 644 ./drips.wav /usr/local/share/openmortal/sound/drips.wav
 /usr/bin/install -c -m 644 ./honk.wav /usr/local/share/openmortal/sound/honk.wav
 /usr/bin/install -c -m 644 ./shu.wav /usr/local/share/openmortal/sound/shu.wav
 /usr/bin/install -c -m 644 ./swoosh.wav /usr/local/share/openmortal/sound/swoosh.wav
 /usr/bin/install -c -m 644 ./ups.wav /usr/local/share/openmortal/sound/ups.wav
 /usr/bin/install -c -m 644 ./autostart.wav /usr/local/share/openmortal/sound/autostart.wav
 /usr/bin/install -c -m 644 ./buzzer_2.wav /usr/local/share/openmortal/sound/buzzer_2.wav
 /usr/bin/install -c -m 644 ./endcountdown_sound.wav /usr/local/share/openmortal/sound/endcountdown_sound.wav
 /usr/bin/install -c -m 644 ./laser.wav /usr/local/share/openmortal/sound/laser.wav
 /usr/bin/install -c -m 644 ./soundmap.txt /usr/local/share/openmortal/sound/soundmap.txt
 /usr/bin/install -c -m 644 ./thump3.voc /usr/local/share/openmortal/sound/thump3.voc
 /usr/bin/install -c -m 644 ./woman_screams.voc /usr/local/share/openmortal/sound/woman_screams.voc
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/sound'
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/sound'
Making install in characters
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/characters'
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data/characters'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/local/share/openmortal/characters
 /usr/bin/install -c -m 644 ./Agent.dat /usr/local/share/openmortal/characters/Agent.dat
 /usr/bin/install -c -m 644 ./Cumi.pl /usr/local/share/openmortal/characters/Cumi.pl
 /usr/bin/install -c -m 644 ./Jacint.dat.txt /usr/local/share/openmortal/characters/Jacint.dat.txt
 /usr/bin/install -c -m 644 ./Macy.jpg /usr/local/share/openmortal/characters/Macy.jpg
 /usr/bin/install -c -m 644 ./Agent.dat.txt /usr/local/share/openmortal/characters/Agent.dat.txt
 /usr/bin/install -c -m 644 ./Dani.dat /usr/local/share/openmortal/characters/Dani.dat
 /usr/bin/install -c -m 644 ./Jacint.icon.png /usr/local/share/openmortal/characters/Jacint.icon.png
 /usr/bin/install -c -m 644 ./Macy.pl /usr/local/share/openmortal/characters/Macy.pl
 /usr/bin/install -c -m 644 ./Agent.full.png /usr/local/share/openmortal/characters/Agent.full.png
 /usr/bin/install -c -m 644 ./Dani.dat.txt /usr/local/share/openmortal/characters/Dani.dat.txt
 /usr/bin/install -c -m 644 ./Jacint.pl /usr/local/share/openmortal/characters/Jacint.pl
 /usr/bin/install -c -m 644 ./Misi.full.png /usr/local/share/openmortal/characters/Misi.full.png
 /usr/bin/install -c -m 644 ./Agent.icon.png /usr/local/share/openmortal/characters/Agent.icon.png
 /usr/bin/install -c -m 644 ./Dani.full.png /usr/local/share/openmortal/characters/Dani.full.png
 /usr/bin/install -c -m 644 ./Jozsi.dat /usr/local/share/openmortal/characters/Jozsi.dat
 /usr/bin/install -c -m 644 ./Misi.icon.png /usr/local/share/openmortal/characters/Misi.icon.png
 /usr/bin/install -c -m 644 ./Agent.jpg /usr/local/share/openmortal/characters/Agent.jpg
 /usr/bin/install -c -m 644 ./Dani.icon.png /usr/local/share/openmortal/characters/Dani.icon.png
 /usr/bin/install -c -m 644 ./Jozsi.dat.txt /usr/local/share/openmortal/characters/Jozsi.dat.txt
 /usr/bin/install -c -m 644 ./Misi.jpg /usr/local/share/openmortal/characters/Misi.jpg
 /usr/bin/install -c -m 644 ./Ulmar.dat /usr/local/share/openmortal/characters/Ulmar.dat
 /usr/bin/install -c -m 644 ./Agent.pl /usr/local/share/openmortal/characters/Agent.pl
 /usr/bin/install -c -m 644 ./Dani.jpg /usr/local/share/openmortal/characters/Dani.jpg
 /usr/bin/install -c -m 644 ./Jozsi.icon.png /usr/local/share/openmortal/characters/Jozsi.icon.png
 /usr/bin/install -c -m 644 ./Mrsmith.dat /usr/local/share/openmortal/characters/Mrsmith.dat
 /usr/bin/install -c -m 644 ./Ulmar.dat.txt /usr/local/share/openmortal/characters/Ulmar.dat.txt
 /usr/bin/install -c -m 644 ./Ambrus.dat /usr/local/share/openmortal/characters/Ambrus.dat
 /usr/bin/install -c -m 644 ./Dani.pl /usr/local/share/openmortal/characters/Dani.pl
 /usr/bin/install -c -m 644 ./Jozsi.pl /usr/local/share/openmortal/characters/Jozsi.pl
 /usr/bin/install -c -m 644 ./Mrsmith.dat.txt /usr/local/share/openmortal/characters/Mrsmith.dat.txt
 /usr/bin/install -c -m 644 ./Ulmar.full.png /usr/local/share/openmortal/characters/Ulmar.full.png
 /usr/bin/install -c -m 644 ./Ambrus.dat.txt /usr/local/share/openmortal/characters/Ambrus.dat.txt
 /usr/bin/install -c -m 644 ./Descant.dat /usr/local/share/openmortal/characters/Descant.dat
 /usr/bin/install -c -m 644 ./Judy.dat /usr/local/share/openmortal/characters/Judy.dat
 /usr/bin/install -c -m 644 ./Mrsmith.icon.png /usr/local/share/openmortal/characters/Mrsmith.icon.png
 /usr/bin/install -c -m 644 ./Ulmar.icon.png /usr/local/share/openmortal/characters/Ulmar.icon.png
 /usr/bin/install -c -m 644 ./Ambrus.full.png /usr/local/share/openmortal/characters/Ambrus.full.png
 /usr/bin/install -c -m 644 ./Descant.dat.txt /usr/local/share/openmortal/characters/Descant.dat.txt
 /usr/bin/install -c -m 644 ./Judy.dat.txt /usr/local/share/openmortal/characters/Judy.dat.txt
 /usr/bin/install -c -m 644 ./Mrsmith.pl /usr/local/share/openmortal/characters/Mrsmith.pl
 /usr/bin/install -c -m 644 ./Ulmar.jpg /usr/local/share/openmortal/characters/Ulmar.jpg
 /usr/bin/install -c -m 644 ./Ambrus.icon.png /usr/local/share/openmortal/characters/Ambrus.icon.png
 /usr/bin/install -c -m 644 ./Descant.full.png /usr/local/share/openmortal/characters/Descant.full.png
 /usr/bin/install -c -m 644 ./Judy.full.png /usr/local/share/openmortal/characters/Judy.full.png
 /usr/bin/install -c -m 644 ./Sirpi.dat /usr/local/share/openmortal/characters/Sirpi.dat
 /usr/bin/install -c -m 644 ./Ulmar.pl /usr/local/share/openmortal/characters/Ulmar.pl
 /usr/bin/install -c -m 644 ./Ambrus.jpg /usr/local/share/openmortal/characters/Ambrus.jpg
 /usr/bin/install -c -m 644 ./Descant.icon.png /usr/local/share/openmortal/characters/Descant.icon.png
 /usr/bin/install -c -m 644 ./Judy.icon.png /usr/local/share/openmortal/characters/Judy.icon.png
 /usr/bin/install -c -m 644 ./Sirpi.dat.txt /usr/local/share/openmortal/characters/Sirpi.dat.txt
 /usr/bin/install -c -m 644 ./UPi.dat /usr/local/share/openmortal/characters/UPi.dat
 /usr/bin/install -c -m 644 ./Ambrus.pl /usr/local/share/openmortal/characters/Ambrus.pl
 /usr/bin/install -c -m 644 ./Descant.jpg /usr/local/share/openmortal/characters/Descant.jpg
 /usr/bin/install -c -m 644 ./Judy.jpg /usr/local/share/openmortal/characters/Judy.jpg
 /usr/bin/install -c -m 644 ./Sirpi.full.png /usr/local/share/openmortal/characters/Sirpi.full.png
 /usr/bin/install -c -m 644 ./UPi.dat.txt /usr/local/share/openmortal/characters/UPi.dat.txt
 /usr/bin/install -c -m 644 ./Bence.dat /usr/local/share/openmortal/characters/Bence.dat
 /usr/bin/install -c -m 644 ./Descant.pl /usr/local/share/openmortal/characters/Descant.pl
 /usr/bin/install -c -m 644 ./Judy.pl /usr/local/share/openmortal/characters/Judy.pl
 /usr/bin/install -c -m 644 ./Sirpi.icon.png /usr/local/share/openmortal/characters/Sirpi.icon.png
 /usr/bin/install -c -m 644 ./UPi.full.png /usr/local/share/openmortal/characters/UPi.full.png
 /usr/bin/install -c -m 644 ./Bence.dat.txt /usr/local/share/openmortal/characters/Bence.dat.txt
 /usr/bin/install -c -m 644 ./Elf.full.png /usr/local/share/openmortal/characters/Elf.full.png
 /usr/bin/install -c -m 644 ./Kinga.dat /usr/local/share/openmortal/characters/Kinga.dat
 /usr/bin/install -c -m 644 ./Sirpi.jpg /usr/local/share/openmortal/characters/Sirpi.jpg
 /usr/bin/install -c -m 644 ./UPi.icon.png /usr/local/share/openmortal/characters/UPi.icon.png
 /usr/bin/install -c -m 644 ./Bence.full.png /usr/local/share/openmortal/characters/Bence.full.png
 /usr/bin/install -c -m 644 ./Elf.icon.png /usr/local/share/openmortal/characters/Elf.icon.png
 /usr/bin/install -c -m 644 ./Kinga.dat.txt /usr/local/share/openmortal/characters/Kinga.dat.txt
 /usr/bin/install -c -m 644 ./Sirpi.pl /usr/local/share/openmortal/characters/Sirpi.pl
 /usr/bin/install -c -m 644 ./UPi.jpg /usr/local/share/openmortal/characters/UPi.jpg
 /usr/bin/install -c -m 644 ./Bence.icon.png /usr/local/share/openmortal/characters/Bence.icon.png
 /usr/bin/install -c -m 644 ./Elf.jpg /usr/local/share/openmortal/characters/Elf.jpg
 /usr/bin/install -c -m 644 ./Kinga.full.png /usr/local/share/openmortal/characters/Kinga.full.png
 /usr/bin/install -c -m 644 ./Sleepy.dat /usr/local/share/openmortal/characters/Sleepy.dat
 /usr/bin/install -c -m 644 ./UPi.pl /usr/local/share/openmortal/characters/UPi.pl
 /usr/bin/install -c -m 644 ./Bence.jpg /usr/local/share/openmortal/characters/Bence.jpg
 /usr/bin/install -c -m 644 ./Grizli.dat /usr/local/share/openmortal/characters/Grizli.dat
 /usr/bin/install -c -m 644 ./Kinga.icon.png /usr/local/share/openmortal/characters/Kinga.icon.png
 /usr/bin/install -c -m 644 ./Sleepy.dat.txt /usr/local/share/openmortal/characters/Sleepy.dat.txt
 /usr/bin/install -c -m 644 ./Zoli.dat /usr/local/share/openmortal/characters/Zoli.dat
 /usr/bin/install -c -m 644 ./Bence.pl /usr/local/share/openmortal/characters/Bence.pl
 /usr/bin/install -c -m 644 ./Grizli.dat.txt /usr/local/share/openmortal/characters/Grizli.dat.txt
 /usr/bin/install -c -m 644 ./Kinga.jpg /usr/local/share/openmortal/characters/Kinga.jpg
 /usr/bin/install -c -m 644 ./Sleepy.icon.png /usr/local/share/openmortal/characters/Sleepy.icon.png
 /usr/bin/install -c -m 644 ./Zoli.dat.txt /usr/local/share/openmortal/characters/Zoli.dat.txt
 /usr/bin/install -c -m 644 ./Cumi.dat /usr/local/share/openmortal/characters/Cumi.dat
 /usr/bin/install -c -m 644 ./Grizli.full.png /usr/local/share/openmortal/characters/Grizli.full.png
 /usr/bin/install -c -m 644 ./Kinga.pl /usr/local/share/openmortal/characters/Kinga.pl
 /usr/bin/install -c -m 644 ./Sleepy.pl /usr/local/share/openmortal/characters/Sleepy.pl
 /usr/bin/install -c -m 644 ./Zoli.full.png /usr/local/share/openmortal/characters/Zoli.full.png
 /usr/bin/install -c -m 644 ./Cumi.dat.txt /usr/local/share/openmortal/characters/Cumi.dat.txt
 /usr/bin/install -c -m 644 ./Grizli.icon.png /usr/local/share/openmortal/characters/Grizli.icon.png
 /usr/bin/install -c -m 644 ./Macy.dat /usr/local/share/openmortal/characters/Macy.dat
 /usr/bin/install -c -m 644 ./STAFF.DAT /usr/local/share/openmortal/characters/STAFF.DAT
 /usr/bin/install -c -m 644 ./Zoli.icon.png /usr/local/share/openmortal/characters/Zoli.icon.png
 /usr/bin/install -c -m 644 ./Cumi.full.png /usr/local/share/openmortal/characters/Cumi.full.png
 /usr/bin/install -c -m 644 ./Grizli.jpg /usr/local/share/openmortal/characters/Grizli.jpg
 /usr/bin/install -c -m 644 ./Macy.dat.txt /usr/local/share/openmortal/characters/Macy.dat.txt
 /usr/bin/install -c -m 644 ./Surba.full.png /usr/local/share/openmortal/characters/Surba.full.png
 /usr/bin/install -c -m 644 ./Zoli.jpg /usr/local/share/openmortal/characters/Zoli.jpg
 /usr/bin/install -c -m 644 ./Cumi.icon.png /usr/local/share/openmortal/characters/Cumi.icon.png
 /usr/bin/install -c -m 644 ./Grizli.pl /usr/local/share/openmortal/characters/Grizli.pl
 /usr/bin/install -c -m 644 ./Macy.full.png /usr/local/share/openmortal/characters/Macy.full.png
 /usr/bin/install -c -m 644 ./Surba.icon.png /usr/local/share/openmortal/characters/Surba.icon.png
 /usr/bin/install -c -m 644 ./Zoli.pl /usr/local/share/openmortal/characters/Zoli.pl
 /usr/bin/install -c -m 644 ./Cumi.jpg /usr/local/share/openmortal/characters/Cumi.jpg
 /usr/bin/install -c -m 644 ./Jacint.dat /usr/local/share/openmortal/characters/Jacint.dat
 /usr/bin/install -c -m 644 ./Macy.icon.png /usr/local/share/openmortal/characters/Macy.icon.png
 /usr/bin/install -c -m 644 ./Surba.jpg /usr/local/share/openmortal/characters/Surba.jpg
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/characters'
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data/characters'
make[2]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
make[3]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/local/share/openmortal
make[3]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
make[2]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
make[1]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/data'
Making install in src
make[1]: Entering directory `/home/rushikesh988/Desktop/openmortal-0.7/src'
c++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/freetype2  -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I/usr/lib/perl/5.12/CORE  -DDATADIR=\"/usr/local/share/openmortal\" -Wall -c OnlineChat.cpp
OnlineChat.cpp:59:2: error: extra qualification &#8216;CChallengeMenu::&#8217; on member &#8216;CChallengeMenu&#8217; [-fpermissive]
make[1]: *** [OnlineChat.o] Error 1
make[1]: Leaving directory `/home/rushikesh988/Desktop/openmortal-0.7/src'
make: *** [install-recursive] Error 1


---

### Post by oldos2er on 2011-11-01
> **rushikesh988 said:**
> bt I have heard that synaptic is removed from 11.10 ??
I was unable to find it ..can u tell me how to start it

Synaptic is in the repositories ```
sudo apt-get update && sudo apt-get install synaptic
```

You might want to start a new thread in here: [http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44) including the terminal output in post #7, include the name of the program and a link to the source code, if possible.

When compiling code in your home folder you *only* should use sudo if you want to install the software system-wide (i.e. sudo make install), not with configure or make.

---

### Post by rushikesh988 on 2011-11-01
> **oldos2er said:**
> Synaptic is in the repositories ```
sudo apt-get update && sudo apt-get install synaptic
```

You might want to start a new thread in here: [http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44) including the terminal output in post #7, include the name of the program and a link to the source code, if possible.

When compiling code in your home folder you *only* should use sudo if you want to install the software system-wide (i.e. sudo make install), not with configure or make.
well thanks I have posted it..
[http://ubuntuforums.org/showthread.php?p=11416990#post11416990]("http://ubuntuforums.org/showthread.php?p=11416990#post11416990")

---

