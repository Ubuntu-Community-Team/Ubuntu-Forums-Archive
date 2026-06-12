---
title: "help bash panel"
date: 2010-10-22
forum: General Help
---

### Post by mage200 on 2010-10-22
here is the most importent part of the file setup.sh
here link to pastebin:
[http://pastebin.com/mwQ1UArH](http://pastebin.com/mwQ1UArH)
and here the part:

[LIST=1]
[*]cd
[*]chmod 777 ../bin/panel
[*]cd ../bin/panel
[*]chmod 775 zikukim
[*]chmod 775 zeva
[*]chmod 775 x-war
[*]chmod 775 Warcraft
[*]chmod 775 tosaf-zombie
[*]chmod 775 superhero
[*]chmod 775 starwars
[*]chmod 775 spector-kick
[*]chmod 775 spector
[*]chmod 775 plugins.ini
[*]chmod 775 SoccerJam
[*]chmod 775 users
[*]chmod 775 users.ini
[*]chmod 775 Sniper-Realism
[*]chmod 775 Smoke-Sprits
[*]chmod 775 slow
[*]chmod 775 skin-mp5
[*]chmod 775 no-hezi
[*]chmod 775 runs
[*]chmod 775 roundsound
[*]chmod 775 rak-knife
[*]chmod 775 pzaza-tarnegolot
[*]chmod 775 pzaza-meshuga
[*]chmod 775 pzaza
[*]chmod 775 PredatorMode
[*]chmod 775 Popcorn
[*]chmod 775 pokemod
[*]chmod 775 ping
[*]chmod 775 pet
[*]chmod 775 no-ip
[*]chmod 775 neshakim-al-gav
[*]chmod 775 neshakim-afim-bavir
[*]chmod 775 miznah
[*]chmod 775 Matrix
[*]chmod 775 mashtin
[*]chmod 775 maps
[*]chmod 775 m16
[*]chmod 775 lizer
[*]chmod 775 kz
[*]chmod 775 kovaim
[*]chmod 775 kolot-eisha
[*]chmod 775 knife
[*]chmod 775 kill
[*]chmod 775 join
[*]chmod 775 jailbreak
[*]chmod 775 jetpack
[*]chmod 775 Idiot
[*]chmod 775 HP-Regeneration
[*]chmod 775 hook
[*]chmod 775 hns
[*]chmod 775 head
[*]chmod 775 hack
[*]chmod 775 gungame
[*]chmod 775 Gladiator
[*]chmod 775 funmod
[*]chmod 775 FrostNades
[*]chmod 775 ffx
[*]chmod 775 elikopter
[*]chmod 775 drop-money
[*]chmod 775 dodgeball
[*]chmod 775 digel
[*]chmod 775 Diablo-Mod
[*]chmod 775 dgalim
[*]chmod 775 deathrun
[*]chmod 775 dam
[*]chmod 775 csdm
[*]chmod 775 colors
[*]chmod 775 clanmod
[*]chmod 775 chiken
[*]chmod 775 buy_c4
[*]chmod 775 BunnyHop
[*]chmod 775 Bouncing-Nades
[*]chmod 775 biohazard-zombie
[*]chmod 775 bazuka
[*]chmod 775 azamot
[*]chmod 775 awp-kick
[*]chmod 775 anti-zoom
[*]chmod 775 anti-chet
[*]chmod 775 amx-super
[*]chmod 775 AMXModX-v1-8
[*]chmod 775 afk-kick
[*]chmod 775 addadmin
[*] 
[*]chmod 777 ../bin/panel-del
[*] 
[*]cd ../bin/panel-del
[*]chmod 775 zikukim
[*]chmod 775 zeva
[*]chmod 775 x-war
[*]chmod 775 Warcraft
[*]chmod 775 tosaf-zombie
[*]chmod 775 superhero
[*]chmod 775 starwars
[*]chmod 775 spector-kick
[*]chmod 775 soccerjam
[*]chmod 775 Sniper-Realism
[*]chmod 775 Smoke-Sprits
[*]chmod 775 slow
[*]chmod 775 skin-mp5
[*]chmod 775 roundsound
[*]chmod 775 rak-knife
[*]chmod 775 pzaza-tarnegolot
[*]chmod 775 pzaza-meshuga
[*]chmod 775 pzaza
[*]chmod 775 PredatorMode
[*]chmod 775 Popcorn
[*]chmod 775 pokemod
[*]chmod 775 ping
[*]chmod 775 pet
[*]chmod 775 no-ip
[*]chmod 775 neshakim-al-gav
[*]chmod 775 neshakim-afim-bavir
[*]chmod 775 miznah
[*]chmod 775 Matrix
[*]chmod 775 mashtin
[*]chmod 775 m16
[*]chmod 775 lizer
[*]chmod 775 kz
[*]chmod 775 kovaim
[*]chmod 775 kolot-eisha
[*]chmod 775 knife
[*]chmod 775 join
[*]chmod 775 jetpack
[*]chmod 775 Idiot
[*]chmod 775 HP-Regeneration
[*]chmod 775 hook
[*]chmod 775 hns
[*]chmod 775 hack
[*]chmod 775 gungame
[*]chmod 775 Gladiator
[*]chmod 775 FrostNades
[*]chmod 775 ffx
[*]chmod 775 elikopter
[*]chmod 775 drop-money
[*]chmod 775 dodgeball
[*]chmod 775 digel
[*]chmod 775 Diablo-Mod
[*]chmod 775 dgalim
[*]chmod 775 dam
[*]chmod 775 csdm
[*]chmod 775 clanmod
[*]chmod 775 chiken
[*]chmod 775 buy_c4
[*]chmod 775 BunnyHop
[*]chmod 775 jailbreak
[*]chmod 775 Bouncing-Nades
[*]chmod 775 bizhard-zombie
[*]chmod 775 bazuka
[*]chmod 775 azamot
[*]chmod 775 awp-kick
[*]chmod 775 anti-zoom
[*]chmod 775 anti-chet
[*]chmod 775 amx-super
[*]chmod 775 afk-kick
[/LIST]
when i try install it on ubantu is say
chmod: cannot access 'afk-kick' file or directory not exist
chmod: cannot access 'amx-super' file or directory not exist
 for all the install is keep say no access 
thank for helpers.

---

### Post by spikoley on 2010-10-22
Run these commands and post the results.

```
sudo updatedb
```
```
locate afk-kick
```
```
locate amx-super
```

---

### Post by mage200 on 2010-10-22
> **spikoley said:**
> Run these commands and post the results.

```
sudo updatedb
``````
locate afk-kick
``````
locate amx-super
```
is keep say 
chmod: cannot access 'anti-zoom' no such file or directory
chmod: cannot access 'bouncing-nades' no such file or directory
chmod: cannot access 'jailbreak' no such file or directory
chmod: cannot access 'azamot' no such file or directory
chmod: cannot access 'awp-kick' no such file or directory
for all the files any idea?

---

