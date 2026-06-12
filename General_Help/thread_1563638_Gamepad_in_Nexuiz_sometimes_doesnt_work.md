---
title: "Gamepad in Nexuiz sometimes doesnt work"
date: 2010-08-29
forum: General Help
---

### Post by afroman10496 on 2010-08-29
Hey all, I know its sorta n00bish to be using a gamepad in nexuiz but sometimes my logitech dual action gamepad doesn't work and sometiems it does -_-

here's my terminal output from playing a single match on the ctf 1 server:
also i highlighted some stuff in red about the gamepad:

```
joe@joe-laptop:~$ nexuiz
Nexuiz Linux 03:50:47 Oct 25 2009 - debug
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (3664 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (18 files)
Added packfile /usr/share/games/nexuiz/data/textures.pk3 (5370 files)
Trying to load library... "libcurl.so.4" - loaded.
[COLOR="Red"]Failed to init SDL joystick subsystem:[/COLOR] 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics26.cfg
execing ctfscoring-div0.cfg
execing balance.cfg
execing effects-normal.cfg
execing turrets.cfg
execing unit_machinegun.cfg
execing unit_hk.cfg
execing unit_hellion.cfg
execing unit_mlrs.cfg
execing unit_flac.cfg
execing unit_fusreac.cfg
execing unit_plasma.cfg
execing unit_plasma2.cfg
execing unit_tesla.cfg
execing unit_phaser.cfg
execing unit_walker.cfg
execing unit_ewheel.cfg
couldn't exec unit_repulsor.cfg
execing config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Client opened a socket on address [0:0:0:0:0:0:0:0]:0
Initializing Video Mode: fullscreen 1280x800x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon 3100 Graphics 
GL_VERSION: 3.2.9756 Compatibility Profile Context
1 SDL joystick(s) found:
[COLOR="#ff0000"]joystick #0: opened "Logitech Logitech Dual Action" with 4 axes, 12 buttons, 0 balls[/COLOR]
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 2048
Obtained audio specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 1024
Sound format: 48000Hz, 2 channels, 16 bits per sample
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized

Trying to connect...
"challenge vhO`R>GzujZ" received, sending connect request back to 74.86.235.146:26017
Got challenge response
Accepted

Connection accepted to 74.86.235.146:26017
--> client to server keepalive
<-- server to client keepalive

Server: Nexuiz build 08:38:35 Oct  1 2009 - release (progs 15194 crc)

<===================================>

Blue Sky - A quickmap by Strahlemann CTF'ed by djSupport
CDAudio: Bad track number 0.
--> client to server keepalive
<-- server to client keepalive
Added packfile /home/joe/.nexuiz/data/dlcache/blueskyctf_b7.pk3 (22 files)
Added packfile /home/joe/.nexuiz/data/dlcache/q3-nexuiz_compatpack_gpl.pk3 (1649 files)
Shader 'textures/liquids/protolava' already defined, ignoring mismatching redeclaration
Shader 'textures/liquids/clear_ripple3' already defined, ignoring mismatching redeclaration
Shader 'textures/liquids/slime1' already defined, ignoring mismatching redeclaration
Shader 'textures/sfx/beam_waterlight1' already defined, ignoring mismatching redeclaration
Shader 'textures/sfx/pentagramfloor' already defined, ignoring mismatching redeclaration
Shader 'textures/skies/blacksky' already defined, ignoring mismatching redeclaration
Shader 'textures/skies/xblacksky' already defined, ignoring mismatching redeclaration
Shader 'textures/skies/hellsky' already defined, ignoring mismatching redeclaration
maps/blueskyctf_b7.bsp: could not load texture "textures/NULL"
CSQC csprogs.dat loaded (crc=61283, size=408476)
Draw_CachePic: failed to load gfx/blueskyctf_b7_radar.tga
Winx has been vaporized by Carolina
[DieTunichtguten] Fjant : vem e sverige?
Cannot change to a larger team
<-- server to client keepalive
--> client to server keepalive
Sweden: ja
FAILURE connected and joined the Red Team
FAILURE is spectating now
couldn't exec maps/blueskyctf_b7.cfg
PostInit
    maxclients = 20
Mailboxhead almost dodged Carolina's rocket
Mailboxhead lost the RED flag
FAILURE is playing now
Sweden: jag
WitchKing has been vaporized by Sweden
You got the Heavy Laser Assault Cannon
Patoruzu Carioca has been vaporized by Sweden
Sweden has 3 frags in a row
Sweden made a TRIPLE FRAG
The RED flag has returned to base
scape has been vaporized by Winx
Dawid was in the wrong place
<=>SloggerKhan[MP]<=> captured the BLUE flag in 73.80, failing to break Duke's record of 17.70 seconds
helldiver450 got too close to Carolina's rocket
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
[DieTunichtguten] Fjant : jo men har du natt normalt nic?
Carolina got too close to Mailboxhead's rocket
Carolina's 3 kill spree was ended by Mailboxhead
FAILURE has been vaporized by Sweden
Sweden has 4 frags in a row
Winx got the RED flag
<Info:> "Xonotic Testers needed! http://www.nullgaming.com/testing/" 
[c]Argento connected and joined the Blue Team
[c]Argento is spectating now
checker_kid#	 has been vaporized by Winx
WitchKing got too close to GrasshopperQ's blue beam
Dratz_C is playing now
Winx was gunned by scape
Winx lost the RED flag
scape returned the RED flag
You got the Heavy Laser Assault Cannon
Dawid got too close to <=>SloggerKhan[MP]<=>'s rocket
Patoruzu Carioca was lasered to death by Sweden
Sweden has 5 frags in a row
Sweden unleashes RAGE
You got the Machine Gun
[c]Argento is playing now
Winx was thrown into a world of hurt by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 3 frags in a row
<=>SloggerKhan[MP]<=> made a TRIPLE FRAG
Patoruzu Carioca disconnected
checker_kid#	 was cut down by GrasshopperQ
GrasshopperQ was lasered to death by Carolina
GrasshopperQ has changed from Blue Team to Red Team
<=>SloggerKhan[MP]<=> got the BLUE flag
helldiver450 has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 4 frags in a row
Dawid was gunned by WitchKing
checker_kid#	 was in the wrong place
<=>SloggerKhan[MP]<=> has been vaporized by Sweden
<=>SloggerKhan[MP]<=>'s 4 kill spree was ended by Sweden
Sweden has 6 frags in a row
<=>SloggerKhan[MP]<=> lost the BLUE flag
Mailboxhead mows down a team mate
Sweden's 6 kill spree was ended by a team mate!
Sweden: whew
[c]Argento has been vaporized by scape
<=>SloggerKhan[MP]<=> picked up the BLUE flag
FAILURE almost dodged Mailboxhead's rocket
Carolina got too close to Mailboxhead's rocket
(Carolina) Yikes Danger => (l:Electro)
You got the Rocket Launcher
<=>SloggerKhan[MP]<=> captured the BLUE flag in 26.35, failing to break Duke's record of 17.70 seconds
Sweden: jag pratar lite svenska
Mailboxhead got the RED flag
Dawid was gunned by GrasshopperQ
The Grappling Hook is NOT AVAILABLE in this map
WitchKing exploded
Mailboxhead was gunned by <=>SloggerKhan[MP]<=>
Mailboxhead lost the RED flag
<=>SloggerKhan[MP]<=> returned the RED flag
Mailboxhead ate Carolina's rocket
Winx got too close to Carolina's rocket
Carolina got the BLUE flag
[DieTunichtguten] Fjant : ok u got annother nick that i might know?
FAILURE was gunned by Dawid
[c]<=>W@RF@RE<=>: hey arg , u suck
Sweden was thrown into a world of hurt by Carolina
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
checker_kid#	 ate helldiver450's grenade
Dratz_C was gunned by Carolina
Carolina has 4 frags in a row
You got the Rocket Launcher
Sweden: me?
[c]Argento: hey warfy ur right
Dawid got too close to Carolina's rocket
Carolina has 5 frags in a row
Carolina unleashes RAGE
[DieTunichtguten] Fjant : ye
FAILURE exploded
WitchKing was in the wrong place
checker_kid#	 almost dodged Mailboxhead's rocket
Winx hit the ground with a crunch
]vcall gotomap miniman
* FAILURE calls a vote for gotomap minimanq3_r3
[c]Argento was in the wrong place
Carolina: ahah
Sweden: i was playing as ellipses yesterday and today
Carolina captured the BLUE flag in 29.90, failing to break Duke's record of 17.70 seconds
[c]<=>W@RF@RE<=>: he has had LOADS fjant
[c]Argento is spectating now
You got the Electro
You got the Mortar
helldiver450 has been vaporized by GrasshopperQ
<=>SloggerKhan[MP]<=> got the BLUE flag
Carolina got too close to Mailboxhead's rocket
Carolina's 5 kill spree was ended by Mailboxhead
Carolina: [PwNt]
Carolina: f2'd
scape: this map makes me sick
Carolina: vcall soemthing else please
Dawid got the RED flag
[c]Argento: Carolina ???
[c]<=>W@RF@RE<=>: face admittign his inner woman
[c]Argento: face
[DieTunichtguten] Fjant : ok then i dont think ive seen u play before
FAILURE was cut down by Winx
Dratz_C got too close to Carolina's rocket
Sweden: how about <fragit> or <teams>
helldiver450 was lasered to death by Carolina
Sweden was thrown into a world of hurt by WitchKing
WitchKing was thrown into a world of hurt by Dawid
* vote results: 4:3 (6 needed), 0 didn't care, 9 didn't vote
* FAILURE's vote for gotomap minimanq3_r3 was rejected
<=>SloggerKhan[MP]<=> was gunned by Winx
<=>SloggerKhan[MP]<=> lost the BLUE flag
Winx has been vaporized by scape
scape has 3 frags in a row
scape made a TRIPLE FRAG
* [c]Argento calls a vote for timelimit -1
Sweden: <> with green and yellow like the info thing
You rejected the vote.
GrasshopperQ was in the wrong place
FAILURE was in the wrong place
Mailboxhead returned the BLUE flag
Mailboxhead got too close to Carolina's rocket
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
You got the Machine Gun
Carolina: noooooo
[c]Argento: cookies.com
Sweden has been vaporized by <=>SloggerKhan[MP]<=>
WitchKing was pummeled by Mailboxhead
<Info:> "Wanna see what changed in Xonotic? Help test it http://www.nullgaming.com/testing/" 
Dawid captured the RED flag in 66.35, failing to break Duke's record of 17.70 seconds
FAILURE mows down a team mate
scape was pummeled by helldiver450
scape's 3 kill spree was ended by helldiver450
You got the Hagar
Dratz_C was in the wrong place
Winx was lasered to death by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> got the BLUE flag
Dawid got too close to Carolina's rocket
Carolina has 4 frags in a row
Sweden lasered himself to hell
GrasshopperQ exploded
* vote results: 5:3 (7 needed), 0 didn't care, 8 didn't vote
* [c]Argento's vote for timelimit -1 was rejected
<=>SloggerKhan[MP]<=> captured the BLUE flag in 24.00, failing to break Duke's record of 17.70 seconds
Winx was grounded by Carolina
Carolina has 5 frags in a row
Carolina unleashes RAGE
[c]Argento: 8 didnt vote
FAILURE ate Dratz_C's rocket
Dratz_C got the RED flag
[c]Argento: why?
Sweden has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 3 frags in a row
<=>SloggerKhan[MP]<=> made a TRIPLE FRAG
You got the Machine Gun
GrasshopperQ was in the wrong place
You got the Rocket Launcher
Sweden: me dont like this map
[c]<=>W@RF@RE<=>: yes mostly nubs here atm ...including you
Carolina got the BLUE flag
GrasshopperQ was thrown into a world of hurt by Dratz_C
You got the Electro
[c]Argento: haha
(GrasshopperQ) ME DONT CARE
WitchKing got too close to Mailboxhead's rocket
[c]Argento: im noob, i know
FAILURE exploded
Dawid was lasered to death by Carolina
Carolina has 6 frags in a row
Dratz_C has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 4 frags in a row
Dratz_C lost the RED flag
Winx was grounded by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 5 frags in a row
<=>SloggerKhan[MP]<=> unleashes RAGE
]vcall gotomap miniman
* FAILURE calls a vote for gotomap minimanq3_r3
<=>SloggerKhan[MP]<=> returned the RED flag
helldiver450 has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 6 frags in a row
[c]Argento: ofcourse ur noob too
You got the Electro
Carolina captured the BLUE flag in 30.80, failing to break Duke's record of 17.70 seconds
Carolina almost dodged Mailboxhead's rocket
Carolina's 6 kill spree was ended by Mailboxhead
Mailboxhead has 3 frags in a row
Mailboxhead made a TRIPLE FRAG
Mailboxhead got the RED flag
You got the Rocket Launcher
<=>SloggerKhan[MP]<=> got the BLUE flag
Dratz_C disconnected
GrasshopperQ was in the wrong place
GrasshopperQ has changed from Red Team to Blue Team
[c]<=>W@RF@RE<=>: ubernoob
FAILURE was in the wrong place
FAILURE mows down a team mate
<=>SloggerKhan[MP]<=>'s 6 kill spree was ended by a team mate!
<=>SloggerKhan[MP]<=> lost the BLUE flag
Sweden mows down a team mate
Mailboxhead's 3 kill spree was ended by a team mate!
Mailboxhead lost the RED flag
Winx picked up the RED flag
<=>SloggerKhan[MP]<=>: wtf
The BLUE flag has returned to base
Sweden: sorry
Dawid ate checker_kid#	's rocket
You got the Machine Gun
You got the Rocket Launcher
GrasshopperQ mows down a team mate
Winx lost the RED flag
scape got the BLUE flag
helldiver450 picked up the RED flag
[DieTunichtguten] Fjant  is playing now
You got the Electro
[c]Argento: Sweden where ru from?
[c]Argento: hha
Sweden: usa
helldiver450 has been vaporized by Carolina
helldiver450 lost the RED flag
Carolina got too close to Mailboxhead's rocket
(Carolina) Our Flag! I see that bastard!=> (l:Electro)
(Carolina) Our Flag! I see that bastard!=> (l:Electro)
helldiver450: FUUUCK
Mailboxhead picked up the RED flag
* vote results: 6:4 (8 needed), 0 didn't care, 5 didn't vote
* FAILURE's vote for gotomap minimanq3_r3 was rejected
FAILURE was cut down by Winx
Carolina: f2'd
* Carolina calls a vote for gotomap Equinox
[c]<=>W@RF@RE<=>: he expected you to say sweden LOL
You rejected the vote.
[c]Argento: yeah
You got the Machine Gun
WitchKing was cut down by Winx
(checker_kid#	) was soll der schei_ man
[DieTunichtguten] Fjant  mows down a team mate
Winx almost dodged <=>SloggerKhan[MP]<=>'s grenade
[c]Argento: he told usa
You got the Rocket Launcher
[c]<=>W@RF@RE<=>: f2'd
[c]Argento: he told me*
[DieTunichtguten] Fjant  was lasered to death by Carolina
(scape) fc at blue flag
You got the Electro
WitchKing disconnected
(Carolina) 10-4!!
(Carolina) attacking enemy base (l:Electro) (h:75 a:36 w:Electro)
GrasshopperQ has changed from Blue Team to Red Team
Sweden: but i live in sweden...  i once nicked as 'stuck in sweden'
[c]Argento: GrasshopperQ ??
[c]<=>W@RF@RE<=>: look atthat idiot
<Info:> "I once dated a girl who tested Xonotic. She put out. http://www.nullgaming.com/testing/" 
(Carolina) quad|shield is spawning..
Dawid has been vaporized by <=>SloggerKhan[MP]<=>
Winx almost dodged scape's grenade
* vote results: 4:4 (7 needed), 0 didn't care, 6 didn't vote
* Carolina's vote for gotomap Equinox was rejected
[DieTunichtguten] Fjant  ate Carolina's rocket
Mailboxhead has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 3 frags in a row
<=>SloggerKhan[MP]<=> made a TRIPLE FRAG
Mailboxhead lost the RED flag
Sweden picked up the RED flag
[c]<=>W@RF@RE<=>: stnds right in own fc's face so he cant defend hisself
<=>SloggerKhan[MP]<=> was blasted by Sweden's blue beam
<=>SloggerKhan[MP]<=>'s 3 kill spree was ended by Sweden
<=>SloggerKhan[MP]<=> was gunned by Mailboxhead
[c]Argento: where do u at Sweden ?
helldiver450 has been vaporized by Carolina
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
Sweden: goteborg
[c]Argento: now tell me Sweden
FAILURE was in the wrong place
[c]Argento: nah
Carolina has been vaporized by Sweden
Carolina's 3 kill spree was ended by Sweden
(Carolina) Our Flag! I see that bastard!=> (l:Strength Powejoe@joe-laptop:~$ nexuiz
Nexuiz Linux 03:50:47 Oct 25 2009 - debug
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (3664 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (18 files)
Added packfile /usr/share/games/nexuiz/data/textures.pk3 (5370 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics26.cfg
execing ctfscoring-div0.cfg
execing balance.cfg
execing effects-normal.cfg
execing turrets.cfg
execing unit_machinegun.cfg
execing unit_hk.cfg
execing unit_hellion.cfg
execing unit_mlrs.cfg
execing unit_flac.cfg
execing unit_fusreac.cfg
execing unit_plasma.cfg
execing unit_plasma2.cfg
execing unit_tesla.cfg
execing unit_phaser.cfg
execing unit_walker.cfg
execing unit_ewheel.cfg
couldn't exec unit_repulsor.cfg
execing config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Client opened a socket on address [0:0:0:0:0:0:0:0]:0
Initializing Video Mode: fullscreen 1280x800x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon 3100 Graphics 
GL_VERSION: 3.2.9756 Compatibility Profile Context
1 SDL joystick(s) found:
joystick #0: opened "Logitech Logitech Dual Action" with 4 axes, 12 buttons, 0 balls
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 2048
Obtained audio specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 1024
Sound format: 48000Hz, 2 channels, 16 bits per sample
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized

Trying to connect...
"challenge vhO`R>GzujZ" received, sending connect request back to 74.86.235.146:26017
Got challenge response
Accepted

Connection accepted to 74.86.235.146:26017
--> client to server keepalive
<-- server to client keepalive

Server: Nexuiz build 08:38:35 Oct  1 2009 - release (progs 15194 crc)

<===================================>

Blue Sky - A quickmap by Strahlemann CTF'ed by djSupport
CDAudio: Bad track number 0.
--> client to server keepalive
<-- server to client keepalive
Added packfile /home/joe/.nexuiz/data/dlcache/blueskyctf_b7.pk3 (22 files)
Added packfile /home/joe/.nexuiz/data/dlcache/q3-nexuiz_compatpack_gpl.pk3 (1649 files)
Shader 'textures/liquids/protolava' already defined, ignoring mismatching redeclaration
Shader 'textures/liquids/clear_ripple3' already defined, ignoring mismatching redeclaration
Shader 'textures/liquids/slime1' already defined, ignoring mismatching redeclaration
Shader 'textures/sfx/beam_waterlight1' already defined, ignoring mismatching redeclaration
Shader 'textures/sfx/pentagramfloor' already defined, ignoring mismatching redeclaration
Shader 'textures/skies/blacksky' already defined, ignoring mismatching redeclaration
Shader 'textures/skies/xblacksky' already defined, ignoring mismatching redeclaration
Shader 'textures/skies/hellsky' already defined, ignoring mismatching redeclaration
maps/blueskyctf_b7.bsp: could not load texture "textures/NULL"
CSQC csprogs.dat loaded (crc=61283, size=408476)
Draw_CachePic: failed to load gfx/blueskyctf_b7_radar.tga
Winx has been vaporized by Carolina
[DieTunichtguten] Fjant : vem e sverige?
Cannot change to a larger team
<-- server to client keepalive
--> client to server keepalive
Sweden: ja
FAILURE connected and joined the Red Team
FAILURE is spectating now
couldn't exec maps/blueskyctf_b7.cfg
PostInit
    maxclients = 20
Mailboxhead almost dodged Carolina's rocket
Mailboxhead lost the RED flag
FAILURE is playing now
Sweden: jag
WitchKing has been vaporized by Sweden
You got the Heavy Laser Assault Cannon
Patoruzu Carioca has been vaporized by Sweden
Sweden has 3 frags in a row
Sweden made a TRIPLE FRAG
The RED flag has returned to base
scape has been vaporized by Winx
Dawid was in the wrong place
<=>SloggerKhan[MP]<=> captured the BLUE flag in 73.80, failing to break Duke's record of 17.70 seconds
helldiver450 got too close to Carolina's rocket
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
[DieTunichtguten] Fjant : jo men har du natt normalt nic?
Carolina got too close to Mailboxhead's rocket
Carolina's 3 kill spree was ended by Mailboxhead
FAILURE has been vaporized by Sweden
Sweden has 4 frags in a row
Winx got the RED flag
<Info:> "Xonotic Testers needed! http://www.nullgaming.com/testing/" 
[c]Argento connected and joined the Blue Team
[c]Argento is spectating now
checker_kid#	 has been vaporized by Winx
WitchKing got too close to GrasshopperQ's blue beam
Dratz_C is playing now
Winx was gunned by scape
Winx lost the RED flag
scape returned the RED flag
You got the Heavy Laser Assault Cannon
Dawid got too close to <=>SloggerKhan[MP]<=>'s rocket
Patoruzu Carioca was lasered to death by Sweden
Sweden has 5 frags in a row
Sweden unleashes RAGE
You got the Machine Gun
[c]Argento is playing now
Winx was thrown into a world of hurt by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 3 frags in a row
<=>SloggerKhan[MP]<=> made a TRIPLE FRAG
Patoruzu Carioca disconnected
checker_kid#	 was cut down by GrasshopperQ
GrasshopperQ was lasered to death by Carolina
GrasshopperQ has changed from Blue Team to Red Team
<=>SloggerKhan[MP]<=> got the BLUE flag
helldiver450 has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 4 frags in a row
Dawid was gunned by WitchKing
checker_kid#	 was in the wrong place
<=>SloggerKhan[MP]<=> has been vaporized by Sweden
<=>SloggerKhan[MP]<=>'s 4 kill spree was ended by Sweden
Sweden has 6 frags in a row
<=>SloggerKhan[MP]<=> lost the BLUE flag
Mailboxhead mows down a team mate
Sweden's 6 kill spree was ended by a team mate!
Sweden: whew
[c]Argento has been vaporized by scape
<=>SloggerKhan[MP]<=> picked up the BLUE flag
FAILURE almost dodged Mailboxhead's rocket
Carolina got too close to Mailboxhead's rocket
(Carolina) Yikes Danger => (l:Electro)
You got the Rocket Launcher
<=>SloggerKhan[MP]<=> captured the BLUE flag in 26.35, failing to break Duke's record of 17.70 seconds
Sweden: jag pratar lite svenska
Mailboxhead got the RED flag
Dawid was gunned by GrasshopperQ
The Grappling Hook is NOT AVAILABLE in this map
WitchKing exploded
Mailboxhead was gunned by <=>SloggerKhan[MP]<=>
Mailboxhead lost the RED flag
<=>SloggerKhan[MP]<=> returned the RED flag
Mailboxhead ate Carolina's rocket
Winx got too close to Carolina's rocket
Carolina got the BLUE flag
[DieTunichtguten] Fjant : ok u got annother nick that i might know?
FAILURE was gunned by Dawid
[c]<=>W@RF@RE<=>: hey arg , u suck
Sweden was thrown into a world of hurt by Carolina
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
checker_kid#	 ate helldiver450's grenade
Dratz_C was gunned by Carolina
Carolina has 4 frags in a row
You got the Rocket Launcher
Sweden: me?
[c]Argento: hey warfy ur right
Dawid got too close to Carolina's rocket
Carolina has 5 frags in a row
Carolina unleashes RAGE
[DieTunichtguten] Fjant : ye
FAILURE exploded
WitchKing was in the wrong place
checker_kid#	 almost dodged Mailboxhead's rocket
Winx hit the ground with a crunch
]vcall gotomap miniman
* FAILURE calls a vote for gotomap minimanq3_r3
[c]Argento was in the wrong place
Carolina: ahah
Sweden: i was playing as ellipses yesterday and today
Carolina captured the BLUE flag in 29.90, failing to break Duke's record of 17.70 seconds
[c]<=>W@RF@RE<=>: he has had LOADS fjant
[c]Argento is spectating now
You got the Electro
You got the Mortar
helldiver450 has been vaporized by GrasshopperQ
<=>SloggerKhan[MP]<=> got the BLUE flag
Carolina got too close to Mailboxhead's rocket
Carolina's 5 kill spree was ended by Mailboxhead
Carolina: [PwNt]
Carolina: f2'd
scape: this map makes me sick
Carolina: vcall soemthing else please
Dawid got the RED flag
[c]Argento: Carolina ???
[c]<=>W@RF@RE<=>: face admittign his inner woman
[c]Argento: face
[DieTunichtguten] Fjant : ok then i dont think ive seen u play before
FAILURE was cut down by Winx
Dratz_C got too close to Carolina's rocket
Sweden: how about <fragit> or <teams>
helldiver450 was lasered to death by Carolina
Sweden was thrown into a world of hurt by WitchKing
WitchKing was thrown into a world of hurt by Dawid
* vote results: 4:3 (6 needed), 0 didn't care, 9 didn't vote
* FAILURE's vote for gotomap minimanq3_r3 was rejected
<=>SloggerKhan[MP]<=> was gunned by Winx
<=>SloggerKhan[MP]<=> lost the BLUE flag
Winx has been vaporized by scape
scape has 3 frags in a row
scape made a TRIPLE FRAG
* [c]Argento calls a vote for timelimit -1
Sweden: <> with green and yellow like the info thing
You rejected the vote.
GrasshopperQ was in the wrong place
FAILURE was in the wrong place
Mailboxhead returned the BLUE flag
Mailboxhead got too close to Carolina's rocket
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
You got the Machine Gun
Carolina: noooooo
[c]Argento: cookies.com
Sweden has been vaporized by <=>SloggerKhan[MP]<=>
WitchKing was pummeled by Mailboxhead
<Info:> "Wanna see what changed in Xonotic? Help test it http://www.nullgaming.com/testing/" 
Dawid captured the RED flag in 66.35, failing to break Duke's record of 17.70 seconds
FAILURE mows down a team mate
scape was pummeled by helldiver450
scape's 3 kill spree was ended by helldiver450
You got the Hagar
Dratz_C was in the wrong place
Winx was lasered to death by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> got the BLUE flag
Dawid got too close to Carolina's rocket
Carolina has 4 frags in a row
Sweden lasered himself to hell
GrasshopperQ exploded
* vote results: 5:3 (7 needed), 0 didn't care, 8 didn't vote
* [c]Argento's vote for timelimit -1 was rejected
<=>SloggerKhan[MP]<=> captured the BLUE flag in 24.00, failing to break Duke's record of 17.70 seconds
Winx was grounded by Carolina
Carolina has 5 frags in a row
Carolina unleashes RAGE
[c]Argento: 8 didnt vote
FAILURE ate Dratz_C's rocket
Dratz_C got the RED flag
[c]Argento: why?
Sweden has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 3 frags in a row
<=>SloggerKhan[MP]<=> made a TRIPLE FRAG
You got the Machine Gun
GrasshopperQ was in the wrong place
You got the Rocket Launcher
Sweden: me dont like this map
[c]<=>W@RF@RE<=>: yes mostly nubs here atm ...including you
Carolina got the BLUE flag
GrasshopperQ was thrown into a world of hurt by Dratz_C
You got the Electro
[c]Argento: haha
(GrasshopperQ) ME DONT CARE
WitchKing got too close to Mailboxhead's rocket
[c]Argento: im noob, i know
FAILURE exploded
Dawid was lasered to death by Carolina
Carolina has 6 frags in a row
Dratz_C has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 4 frags in a row
Dratz_C lost the RED flag
Winx was grounded by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 5 frags in a row
<=>SloggerKhan[MP]<=> unleashes RAGE
]vcall gotomap miniman
* FAILURE calls a vote for gotomap minimanq3_r3
<=>SloggerKhan[MP]<=> returned the RED flag
helldiver450 has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 6 frags in a row
[c]Argento: ofcourse ur noob too
You got the Electro
Carolina captured the BLUE flag in 30.80, failing to break Duke's record of 17.70 seconds
Carolina almost dodged Mailboxhead's rocket
Carolina's 6 kill spree was ended by Mailboxhead
Mailboxhead has 3 frags in a row
Mailboxhead made a TRIPLE FRAG
Mailboxhead got the RED flag
You got the Rocket Launcher
<=>SloggerKhan[MP]<=> got the BLUE flag
Dratz_C disconnected
GrasshopperQ was in the wrong place
GrasshopperQ has changed from Red Team to Blue Team
[c]<=>W@RF@RE<=>: ubernoob
FAILURE was in the wrong place
FAILURE mows down a team mate
<=>SloggerKhan[MP]<=>'s 6 kill spree was ended by a team mate!
<=>SloggerKhan[MP]<=> lost the BLUE flag
Sweden mows down a team mate
Mailboxhead's 3 kill spree was ended by a team mate!
Mailboxhead lost the RED flag
Winx picked up the RED flag
<=>SloggerKhan[MP]<=>: wtf
The BLUE flag has returned to base
Sweden: sorry
Dawid ate checker_kid#	's rocket
You got the Machine Gun
You got the Rocket Launcher
GrasshopperQ mows down a team mate
Winx lost the RED flag
scape got the BLUE flag
helldiver450 picked up the RED flag
[DieTunichtguten] Fjant  is playing now
You got the Electro
[c]Argento: Sweden where ru from?
[c]Argento: hha
Sweden: usa
helldiver450 has been vaporized by Carolina
helldiver450 lost the RED flag
Carolina got too close to Mailboxhead's rocket
(Carolina) Our Flag! I see that bastard!=> (l:Electro)
(Carolina) Our Flag! I see that bastard!=> (l:Electro)
helldiver450: FUUUCK
Mailboxhead picked up the RED flag
* vote results: 6:4 (8 needed), 0 didn't care, 5 didn't vote
* FAILURE's vote for gotomap minimanq3_r3 was rejected
FAILURE was cut down by Winx
Carolina: f2'd
* Carolina calls a vote for gotomap Equinox
[c]<=>W@RF@RE<=>: he expected you to say sweden LOL
You rejected the vote.
[c]Argento: yeah
You got the Machine Gun
WitchKing was cut down by Winx
(checker_kid#	) was soll der schei_ man
[DieTunichtguten] Fjant  mows down a team mate
Winx almost dodged <=>SloggerKhan[MP]<=>'s grenade
[c]Argento: he told usa
You got the Rocket Launcher
[c]<=>W@RF@RE<=>: f2'd
[c]Argento: he told me*
[DieTunichtguten] Fjant  was lasered to death by Carolina
(scape) fc at blue flag
You got the Electro
WitchKing disconnected
(Carolina) 10-4!!
(Carolina) attacking enemy base (l:Electro) (h:75 a:36 w:Electro)
GrasshopperQ has changed from Blue Team to Red Team
Sweden: but i live in sweden...  i once nicked as 'stuck in sweden'
[c]Argento: GrasshopperQ ??
[c]<=>W@RF@RE<=>: look atthat idiot
<Info:> "I once dated a girl who tested Xonotic. She put out. http://www.nullgaming.com/testing/" 
(Carolina) quad|shield is spawning..
Dawid has been vaporized by <=>SloggerKhan[MP]<=>
Winx almost dodged scape's grenade
* vote results: 4:4 (7 needed), 0 didn't care, 6 didn't vote
* Carolina's vote for gotomap Equinox was rejected
[DieTunichtguten] Fjant  ate Carolina's rocket
Mailboxhead has been vaporized by <=>SloggerKhan[MP]<=>
<=>SloggerKhan[MP]<=> has 3 frags in a row
<=>SloggerKhan[MP]<=> made a TRIPLE FRAG
Mailboxhead lost the RED flag
Sweden picked up the RED flag
[c]<=>W@RF@RE<=>: stnds right in own fc's face so he cant defend hisself
<=>SloggerKhan[MP]<=> was blasted by Sweden's blue beam
<=>SloggerKhan[MP]<=>'s 3 kill spree was ended by Sweden
<=>SloggerKhan[MP]<=> was gunned by Mailboxhead
[c]Argento: where do u at Sweden ?
helldiver450 has been vaporized by Carolina
Carolina has 3 frags in a row
Carolina made a TRIPLE FRAG
Sweden: goteborg
[c]Argento: now tell me Sweden
FAILURE was in the wrong place
[c]Argento: nah
Carolina has been vaporized by Sweden
Carolina's 3 kill spree was ended by Sweden
(Carolina) Our Flag! I see that bastard!=> (l:Strength Powerup)
(Carolina) Our Flag! I see that bastard!=> (l:Strength Powerup)
[c]Argento: :P
(Carolina) Our Flag! I see that bastard!=> (l:Rocket Launcher)
CSQC unloaded
rup)
(Carolina) Our Flag! I see that bastard!=> (l:Strength Powerup)
[c]Argento: :P
(Carolina) Our Flag! I see that bastard!=> (l:Rocket Launcher)
CSQC unloaded
```

---

