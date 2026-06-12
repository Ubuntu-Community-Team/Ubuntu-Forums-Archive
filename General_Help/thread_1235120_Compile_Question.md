---
title: "Compile Question"
date: 2009-08-08
forum: General Help
---

### Post by AxelMan0 on 2009-08-08
I'm in a bit of a predicament. How would I go about compiling source from subversion that has no configure and no autogen file? Namely Alien Arena 2009

---

### Post by clonne4crw on 2009-08-08
Seeing as it is too much of a pain in the #@$ to download, can you list the files that are in the archive that you have? Is there anything that resembles an installer that is just a shell script that could be run with 'sh'?

---

### Post by AxelMan0 on 2009-08-08
There is a makefile and a whole bunch of .exe and .dlls as if I had downloaded the windows version. There is a file called check-configs in the "linux scripts" directory but it appears to only relate to server info. The readme contains only install information and there is a file called "game.so" in the "data1" directory. I used this command to get it from subversion:

     svn co [SIZE=2]svn://svn.icculus.org/alienarena/trunk

Here is the extremely long list of files from dir -R, sorry about this but thank god for ctrl+f haha. It's too big to attatch it :(.

.:
directory  trunk

./trunk:
Aa1.ico  botconfigurator.exe  crx.exe  fce16.dll   libcurl.dll    Tools
aa.png     botinfo          data1    fce32.dll   oalinst.exe    zlib1.dll
arena     crded              docs     Galaxy.exe  source

./trunk/arena:
default.cfg  game.so  maps.lst    motd.txt  pics    server.cfg

./trunk/arena/pics:

./trunk/botinfo:
^3Marty.cfg         dm-chasmatic.tmp      dm-warmachine2k9.tmp
allbots.tmp         dm-command2k9.tmp      dm-warmachine.tmp
aoa-atlantis.tmp     dm-corrosion.tmp      dm-zion.tmp
aoa-corrosion.tmp    dm-crucible2k8.tmp   dm-zorn.tmp
aoa-frost2k9.tmp     dm-deimos2k9.tmp      Fafa.cfg
aoa-frost.tmp         dm-dismal2k8.tmp      Gamara.cfg
aoa-morpheus.tmp     dm-dread.tmp      Ghidora.cfg
aoa-zorn.tmp         dm-dynamo2k8.tmp      Hedorah.cfg
Astral.cfg         dm-eternal.tmp      Johnny.cfg
Beavis.cfg         dm-europa2k8.tmp      Martian_is_lame.cfg
Butthead.cfg         dm-furious2k8.tmp      Martian_jr.cfg
Cyborg.cfg         dm-horus.tmp      Martian_owns_u.cfg
db-chromium.tmp      dm-invasion.tmp      Mogera.cfg
db-icarus.tmp         dm-leviathan2k8.tmp  Mothra.cfg
db-vesuvius.tmp      dm-liberation.tmp      nav
Destoroyah.cfg         dm-omega2k8.tmp      Real_Martian.cfg
dm-aquous.tmp         dm-saucer2k9.tmp      sample.cfg
dm-atlantis2k8.tmp   dm-saucer.tmp      Squirtney.cfg
dm-babel.tmp         dm-titan2k8.tmp      Stryker.cfg
dm-beyond.tmp         dm-turbo2k8.tmp      team.tmp
dm-bloodfactory.tmp  dm-vesuvius.tmp      Yoz.cfg
dm-chasmatic2k9.tmp  dm-violator.tmp

./trunk/botinfo/nav:
aoa-atlantis.nod    dm-aquous.nod     dm-invasion.nod
aoa-corrosion.nod   dm-atlantis2k8.nod     dm-leviathan2k8.nod
aoa-frost2k9.nod    dm-babel.nod     dm-leviathan.nod
aoa-frost.nod        dm-beyond.nod     dm-liberation.nod
aoa-morpheus.nod    dm-bloodfactory.nod  dm-obsidian2.nod
aoa-zorn.nod        dm-blood.nod     dm-omega2k8.nod
cp-grindery.nod     dm-chasmatic2k9.nod  dm-omega.nod
cp-ribeye.nod        dm-chasmatic.nod     dm-saucer.nod
ctf-atlantis.nod    dm-command2k9.nod     dm-titan2k8.nod
ctf-chromium.nod    dm-corrosion.nod     dm-titan.nod
ctf-corrosion.nod   dm-crucible2k8.nod     dm-turbo2k8.nod
ctf-cryogenic.nod   dm-deimos2k9.nod     dm-vesuvius.nod
ctf-europa2k8.nod   dm-deimos.nod     dm-violator.nod
ctf-frost2k9.nod    dm-dismal2k8.nod     dm-warmachine2k9.nod
ctf-frost.nod        dm-dismal.nod     dm-warmachine.nod
ctf-icarus2.nod     dm-dread.nod     dm-zion.nod
ctf-stronghold.nod  dm-dynamo2k8.nod     dm-zorn.nod
ctf-terminal.nod    dm-dynamo2.nod     tca-corrosion.nod
ctf-titan2k8.nod    dm-eternal.nod     tca-cryogenic.nod
ctf-vesuvius.nod    dm-europa2k8.nod     tca-europa2k8.nod
ctf-zorn.nod        dm-frontier2.nod     tca-frost.nod
db-chromium.nod     dm-furious2k8.nod     tca-titan2k8.nod
db-icarus.nod        dm-grindery.nod     tca-zion.nod
db-vesuvius.nod     dm-horus.nod

./trunk/data1:
default.cfg  game.so      levelshots  models     players  textures
env         gamex86.dll  maps          particles  scripts  vehicles
fonts         gfx      maps.lst    pics     sound

./trunk/data1/env:
alienbk.tga  egyptrt.tga  hellft.tga     seabk.tga     space1rt.tga
aliendn.tga  egyptup.tga  helllf.tga     seadn.tga     space1up.tga
alienft.tga  greenbk.tga  hellrt.tga     seaft.tga     tekcitybk.tga
alienlf.tga  greendn.tga  hellup.tga     sealf.tga     tekcitydn.tga
alienrt.tga  greenft.tga  martianbk.tga  seart.tga     tekcityft.tga
alienup.tga  greenlf.tga  martiandn.tga  seaup.tga     tekcitylf.tga
egyptbk.tga  greenrt.tga  martianft.tga  space1bk.tga  tekcityrt.tga
egyptdn.tga  greenup.tga  martianlf.tga  space1dn.tga  tekcityup.tga
egyptft.tga  hellbk.tga   martianrt.tga  space1ft.tga
egyptlf.tga  helldn.tga   martianup.tga  space1lf.tga

./trunk/data1/fonts:
default.tga  digital.tga  fat.tga

./trunk/data1/gfx:
aaglow.tga         electrics2.tga         noise.tga
adrenalbase.tga         electrics3a.tga     plate5fx.tga
adrenalmask.tga         electrics3b.tga     purpleline.tga
alienarena2gl.tga     electrics3d.tga     quadbase.tga
bannerfx.tga         electrics3.tga         quadmask.tga
bconsole2.tga         electrics.tga         radar
bconsole.tga         flares             rain.tga
beam1.tga         flash_noise.jpg     rayfx.tga
beam2.tga         flash.tga         redcircuit.tga
beamfx.tga         gamarafx.tga         redlightning.tga
blasterfx.tga         glightning.tga         reflect.tga
bluelightning2.tga     gold.tga         rlauncherfx.tga
bluelightning.tga     grapplefx.tga         r_lightning.tga
bubbles.tga         grass.tga         sconsole.tga
caustics.tga         grchrome.tga         shard_fx.tga
chrome2.tga         greencircuit2.tga     shardmask.tga
chrome.tga         greencircuit.tga     skullglow.tga
citymask.tga         greenlightning.tga     smartgunmask.tga
cloudsspace.tga         greenline.tga         sun1.jpg
clouds.tga         hastebase.tga         sun2.jpg
cloudsthick.tga         hastemask.tga         sun.jpg
comp1.tga         hconsole2.tga         tekwallmask.tga
comp2.tga         hconsole3.tga         trim2mask.tga
cpribeyereflection.tga     hconsole.tga         vaporbase.tga
disruptormask.tga     hoverfx.tga         vapormask.tga
distortwave.jpg         leaves1.tga         violatorfx.tga
dmaquousreflection.tga     lightning.tga         water
dmbeyondreflection.tga     m_banner_main_mask.tga  w_distortwave.jpg
dmdreadreflection.tga     menubar1.tga         w_flash_noise.jpg
dmturboreflection.tga     menubar2.tga         wt_distortwave.jpg
e6launchengine_glow.tga  metal3glow.tga         wt_flash_noise.jpg
egypt5_mask.tga         mirrorspec.tga         yellowline.tga

./trunk/data1/gfx/flares:
flare0.tga

./trunk/data1/gfx/radar:
around.tga  radarmap.tga

./trunk/data1/gfx/water:
distort1.tga  normal1.tga

./trunk/data1/levelshots:
aoa-atlantis.jpg   db-icarus.jpg    dm-invasion.jpg
aoa-atlantis.txt   db-icarus.txt    dm-invasion.txt
aoa-corrosion.jpg  db-vesuvius.jpg    dm-leviathan2k8.jpg
aoa-corrosion.txt  db-vesuvius.txt    dm-leviathan2k8.txt
aoa-frost2k9.jpg   dm-aquous.jpg    dm-liberation.jpg
aoa-frost2k9.txt   dm-aquous.txt    dm-liberation.txt
aoa-frost.jpg       dm-atlantis2k8.jpg    dm-omega2k8.jpg
aoa-frost.txt       dm-atlantis2k8.txt    dm-omega2k8.txt
aoa-morpheus.jpg   dm-babel.jpg        dm-omega.jpg
aoa-morpheus.txt   dm-babel.txt        dm-saucer2k9.jpg
aoa-zorn.jpg       dm-beyond.jpg    dm-saucer2k9.txt
aoa-zorn.txt       dm-beyond.txt    dm-saucer.jpg
cft-corrosion.txt  dm-bloodfactory.jpg    dm-saucer.txt
cp-grindery.jpg    dm-bloodfactory.txt    dm-titan2k8.jpg
cp-grindery.txt    dm-chasmatic2k9.jpg    dm-titan2k8.txt
cp-ribeye.jpg       dm-chasmatic2k9.txt    dm-turbo2k8.jpg
cp-ribeye.txt       dm-command2k9.jpg    dm-turbo2k8.txt
ctf-atlantis.jpg   dm-command2k9.txt    dm-vesuvius.jpg
ctf-atlantis.txt   dm-corrosion.jpg    dm-vesuvius.txt
ctf-chromium.jpg   dm-corrosion.txt    dm-violator.jpg
ctf-chromium.txt   dm-crucible2k8.jpg    dm-violator.txt
ctf-corrosion.jpg  dm-crucible2k8.txt    dm-warmachine2k9.jpg
ctf-cryogenic.jpg  dm-crucible.jpg    dm-warmachine2k9.txt
ctf-cryogenic.txt  dm-crucible.txt    dm-warmachine.txt
ctf-europa2k8.jpg  dm-deimos2k9.jpg    dm-zion.jpg
ctf-europa2k8.txt  dm-deimos2k9.txt    dm-zion.txt
ctf-frost2k9.jpg   dm-dismal2k8.jpg    dm-zorn.jpg
ctf-frost2k9.txt   dm-dismal2k8.txt    dm-zorn.txt
ctf-frost.jpg       dm-dread.jpg        tca-corrosion.jpg
ctf-frost.txt       dm-dread.txt        tca-corrosion.txt
ctf-icarus2.jpg    dm-dynamo2k8.jpg    tca-cryogenic.jpg
ctf-icarus2.txt    dm-dynamo2k8.txt    tca-cryogenic.txt
ctf-titan2k8.jpg   dm-eternal.jpg    tca-europa2k8.jpg
ctf-titan2k8.txt   dm-eternal.txt    tca-europa2k8.txt
ctf-vesuvius.jpg   dm-europa2k8.jpg    tca-frost.jpg
ctf-vesuvius.txt   dm-europa2k8.txt    tca-frost.txt
ctf-zorn.jpg       dm-furious2k8.jpg    tca-titan2k8.jpg
ctf-zorn.txt       dm-furious2k8.txt    tca-titan2k8.txt
db-chromium.jpg    dm-horus.jpg        tca-zion.jpg
db-chromium.txt    dm-horus.txt        tca-zion.txt

./trunk/data1/maps:
aoa-atlantis.bsp    db-vesuvius.bsp     dm-saucer2k9.bsp
aoa-corrosion.bsp   dm-aquous.bsp     dm-saucer.bsp
aoa-frost2k9.bsp    dm-atlantis2k8.bsp     dm-titan2k8.bsp
aoa-morpheus.bsp    dm-babel.bsp     dm-turbo2k8.bsp
aoa-zorn.bsp        dm-beyond.bsp     dm-vesuvius.bsp
compile.bat        dm-bloodfactory.bsp  dm-violator.bsp
cp-grindery.bsp     dm-chasmatic2k9.bsp  dm-warmachine2k9.bsp
cp-ribeye.bsp        dm-command2k9.bsp     dm-zion.bsp
ctf-atlantis.bsp    dm-corrosion.bsp     dm-zorn.bsp
ctf-chromium.bsp    dm-crucible2k8.bsp     lighttest.bsp
ctf-corrosion.bsp   dm-deimos2k9.bsp     mapsrc
ctf-cryogenic.bsp   dm-dismal2k8.bsp     meshes
ctf-europa2k8.bsp   dm-dread.bsp     scripts
ctf-frost2k9.bsp    dm-dynamo2k8.bsp     tca-corrosion.bsp
ctf-icarus2.bsp     dm-eternal.bsp     tca-cryogenic.bsp
ctf-stronghold.bsp  dm-europa2k8.bsp     tca-europa2k8.bsp
ctf-terminal.bsp    dm-furious2k8.bsp     tca-europa.bsp
ctf-titan2k8.bsp    dm-horus.bsp     tca-frost.bsp
ctf-vesuvius.bsp    dm-invasion.bsp     tca-titan2k8.bsp
ctf-zorn.bsp        dm-leviathan2k8.bsp  tca-zion.bsp
db-chromium.bsp     dm-liberation.bsp
db-icarus.bsp        dm-omega2k8.bsp

./trunk/data1/maps/mapsrc:
aoa-atlantis.map    dm-beyond.map     dm-leviathan.map
aoa-corrosion.map   dm-bloodfactory.map  dm-liberation.map
aoa-frost2k9.map    dm-bootcamp.map     dm-omega2k8.map
aoa-morpheus.map    dm-chasmatic2k9.map  dm-omega.map
aoa-zorn.map        dm-chasmatic.map     dm-saucer2k9.map
cp-grindery.map     dm-command2k9.map     dm-saucer.map
cp-ribeye.map        dm-command.map     dm-titan2k8.map
ctf-atlantis.map    dm-corrosion.map     dm-titan.map
ctf-chromium.map    dm-crucible.map     dm-turbo2k8.map
ctf-corrosion.map   dm-deimos2k9.map     dm-turbo.map
ctf-cryogenic.map   dm-deimos.map     dm-vesuvius.map
ctf-europa2k8.map   dm-dismal2k8.map     dm-violator.map
ctf-europa.map        dm-dismal.map     dm-warmachine2k9.map
ctf-frost2k9.map    dm-dread.map     dm-warmachine.map
ctf-icarus.map        dm-dynamo2k8.map     dm-zion.map
ctf-titan2k8.map    dm-dynamo2.map     dm-zorn.map
ctf-titan.map        dm-eternal.map     tca-corrosion.map
ctf-vesuvius.map    dm-europa2k8.map     tca-cryogenic.map
ctf-zorn.map        dm-europa.map     tca-europa2k8.map
db-chromium.map     dm-frontier2.map     tca-europa.map
db-icarus.map        dm-furious2k8.map     tca-frost.map
db-vesuvius.map     dm-furious.map     tca-titan2k8.map
dm-aquous.map        dm-grindery.map     tca-titan.map
dm-atlantis2k8.map  dm-horus.map     tca-zion.map
dm-atlantis.map     dm-invasion.map
dm-babel.map        dm-leviathan2k8.map

./trunk/data1/maps/meshes:
arch_fx.tga           dualpipes_normal.jpg  piston_normal.jpg
arch.md2           electrodecover.md2    piston.tga
arch_normal.jpg        electrode.md2         pulsar.md2
arch.tga           electrode.tga         pulsar_normal.jpg
barrel.jpg           flagpad.md2         pulsar.tga
barrel.md2           flagpad_normal.tga    railcarglass.md2
bentconduit.md2        flagpad.tga         railcar.jpg
bignode_fx.tga           generator.jpg         railcarmartian.md2
bignode.jpg           generator.md2         railcar.md2
bignode.md2           generator_normal.jpg  railcarmhelmet.md2
bignode_normal.jpg     hanger.md2         railcar_normal.jpg
bigribpipe.jpg           hanger_normal.jpg     ribtube1.md2
bigribpipe.md2           hanger.tga         ribtube2.md2
bigribpipe_normal.jpg  hangingmartian.md2    ribtube.jpg
brainjarcover.md2      hangingmhelmet.md2    ribtube_normal.jpg
brainjar.md2           hatch.jpg         sconduit1.md2
brainjar_normal.tga    hatch.md2         sconduit2.md2
brainjar.tga           hatch_normal.jpg      scopecover.md2
cables2.md2           injector.jpg         scope.md2
cables3.md2           injector.md2         scope_normal.tga
cables.jpg           injector_normal.jpg   scope.tga
cables.md2           lamp2_fx.tga         spingear_fx.tga
cannister.jpg           lamp2.jpg         spingear.jpg
cannister.md2           lamp2.md2         spingear.md2
cannister_normal.jpg   lamp2_normal.jpg      spingear_normal.jpg
clamps.jpg           martian.jpg         spintube.jpg
clamps.md2           martian.md2         spintube.md2
clamps_normal.jpg      metpipe1.md2         spintube_normal.jpg
cmdconsole_fx.tga      metpipe2.md2         straightconduit.md2
cmdconsole.jpg           metpipe3.md2         toxicbarrell.jpg
cmdconsole.md2           mhelmet.md2         toxicbarrell.md2
cmdconsole_normal.jpg  monitor2.md2         tubecover.md2
conduit.jpg           monitor.jpg         tube.md2
conduit_normal.jpg     monitormask.tga         tube.tga
controls_fx.tga        monitor.md2         unit.jpg
controls.md2           mpa1.jpg             unit.md2
controls_normal.tga    mpa2.jpg             unit_normal.jpg
controls.tga           pipes1.jpg         weaponpad.md2
dome.md2           pipes1_normal.jpg     weaponpad_normal.tga
dualpipes.jpg           pipes.md2         weaponpad.tga
dualpipes.md2           piston.md2

./trunk/data1/maps/scripts:
aoa2.fog        db-vesuvius.fog     dm-invasion.mus
aoa-atlantis.mus    db-vesuvius.mus     dm-leviathan2k8.fog
aoa-corrosion.fog   dm-aquous.fog     dm-leviathan2k8.mus
aoa-corrosion.mus   dm-aquous.mus     dm-liberation.fog
aoa-frost2k9.fog    dm-atlantis2k8.mus     dm-liberation.mus
aoa-frost2k9.mus    dm-babel.fog     dm-omega2k8.mus
aoa-frost.fog        dm-babel.mus     dm-saucer2k9.fog
aoa-frost.mus        dm-beyond.mus     dm-saucer2k9.mus
aoa-morpheus.mus    dm-bloodfactory.fog  dm-saucer.fog
aoa-zorn.mus        dm-bloodfactory.mus  dm-saucer.mus
cp-grindery.mus     dm-chasmatic2k9.fog  dm-titan2k8.mus
cp-ribeye.mus        dm-chasmatic2k9.mus  dm-turbo2k8.fog
ctf-atlantis.mus    dm-chasmatic.mus     dm-turbo2k8.mus
ctf-chromium.mus    dm-command2k9.fog     dm-vesuvius.fog
ctf-corrosion.fog   dm-command2k9.mus     dm-vesuvius.mus
ctf-corrosion.mus   dm-corrosion.fog     dm-violator.mus
ctf-cryogenic.fog   dm-corrosion.mus     dm-warmachine2k9.fog
ctf-cryogenic.mus   dm-crucible2k8.fog     dm-warmachine2k9.mus
ctf-europa2k8.mus   dm-crucible2k8.mus     dm-warmachine.mus
ctf-frost2k9.fog    dm-deimos2k9.mus     dm-zion.mus
ctf-frost2k9.mus    dm-dismal2k8.fog     dm-zorn.mus
ctf-frost.fog        dm-dismal2k8.mus     tca-corrosion.fog
ctf-icarus2.mus     dm-dread.mus     tca-corrosion.mus
ctf-stronghold.mus  dm-dynamo2k8.fog     tca-cryogenic.fog
ctf-terminal.mus    dm-dynamo2k8.mus     tca-cryogenic.mus
ctf-titan2k8.mus    dm-eternal.fog     tca-europa2k8.mus
ctf-vesuvius.fog    dm-eternal.mus     tca-frost.fog
ctf-vesuvius.mus    dm-europa2k8.mus     tca-frost.mus
ctf-zorn.mus        dm-furious2k8.fog     tca-titan2k8.mus
db-chromium.mus     dm-furious2k8.mus     tca-zion.mus
db-icarus.mus        dm-horus.mus     tourney0.fog

./trunk/data1/models:
cow  items  misc  objects  weapons

./trunk/data1/models/cow:
helmet.md2  skin.tga  tris.md2

./trunk/data1/models/items:
adrenaline  ammo  armor  flags    haste  healing    invulner  quaddama  sproing

./trunk/data1/models/items/adrenaline:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/ammo:
bullets  cells    grenades  rockets  shells  skin_normal.tga

./trunk/data1/models/items/ammo/bullets:
medium

./trunk/data1/models/items/ammo/bullets/medium:
skin.tga  tris.md2

./trunk/data1/models/items/ammo/cells:
medium

./trunk/data1/models/items/ammo/cells/medium:
cell.tga  tris.md2

./trunk/data1/models/items/ammo/grenades:
medium

./trunk/data1/models/items/ammo/grenades/medium:
skin.tga  tris.md2

./trunk/data1/models/items/ammo/rockets:
medium

./trunk/data1/models/items/ammo/rockets/medium:
skin.tga  tris.md2

./trunk/data1/models/items/ammo/shells:
medium

./trunk/data1/models/items/ammo/shells/medium:
skin.tga  tris.md2

./trunk/data1/models/items/armor:
body  combat  jacket  shard  skin_normal.tga

./trunk/data1/models/items/armor/body:
skin.tga  tris.md2

./trunk/data1/models/items/armor/combat:
skin.tga  tris.md2

./trunk/data1/models/items/armor/jacket:
skin.tga  tris.md2

./trunk/data1/models/items/armor/shard:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/flags:
blue.tga  flag1.md2  flag2.md2    red.tga

./trunk/data1/models/items/haste:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/healing:
globe  large  medium  small

./trunk/data1/models/items/healing/globe:
skin.tga  tris.md2

./trunk/data1/models/items/healing/large:
skin.tga  tris.md2

./trunk/data1/models/items/healing/medium:
skin.tga  tris.md2

./trunk/data1/models/items/healing/small:
skin.tga  tris.md2

./trunk/data1/models/items/invulner:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/quaddama:
skin_normal.tga  skin.tga  tris.md2  unit.md2

./trunk/data1/models/items/sproing:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/misc:
electrode  lamp  lamp2    pod  receptor  scope  spiderpod  tube

./trunk/data1/models/misc/electrode:
cover.md2  electrode.tga  tris.md2

./trunk/data1/models/misc/lamp:
lamp.tga  tris.md2

./trunk/data1/models/misc/lamp2:
lamp2.tga  tris.md2

./trunk/data1/models/misc/pod:
pod.tga  tris.md2

./trunk/data1/models/misc/receptor:
bulb.md2  receptor.tga    tris.md2

./trunk/data1/models/misc/scope:
cover.md2  scope.tga  tris.md2

./trunk/data1/models/misc/spiderpod:
skin.tga  tris.md2

./trunk/data1/models/misc/tube:
cover.md2  tris.md2  tube.tga

./trunk/data1/models/objects:
blank  debris1    debris3  electroball  gibs   rocket
brass  debris2    dmspot     fireball     laser

./trunk/data1/models/objects/blank:
skin.tga  tris.md2

./trunk/data1/models/objects/brass:
skin.jpg  tris.md2

./trunk/data1/models/objects/debris1:
skin.tga  tris.md2

./trunk/data1/models/objects/debris2:
skin.tga  tris.md2

./trunk/data1/models/objects/debris3:
skin.tga  tris.md2

./trunk/data1/models/objects/dmspot:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/objects/electroball:
skin.tga  tris.md2

./trunk/data1/models/objects/fireball:
skin.tga  tris.md2

./trunk/data1/models/objects/gibs:
mart_gut  skin_normal.jpg  sm_meat

./trunk/data1/models/objects/gibs/mart_gut:
skin.jpg  tris.md2

./trunk/data1/models/objects/gibs/sm_meat:
skin.jpg  tris.md2

./trunk/data1/models/objects/laser:
skin.tga  tris.md2

./trunk/data1/models/objects/rocket:
skin.tga  tris.md2

./trunk/data1/models/weapons:
g_bfg      g_launch  g_rocket  v_bfg    v_hyperb  v_rocket  v_violator
g_chain   g_machn   g_shotg   v_blast  v_machn     v_shotg
g_hyperb  g_rail    g_shotg2  v_chain  v_rail     v_shotg2

./trunk/data1/models/weapons/g_bfg:
tris.md2

./trunk/data1/models/weapons/g_chain:
tris.md2

./trunk/data1/models/weapons/g_hyperb:
cover.md2  tris.md2

./trunk/data1/models/weapons/g_launch:
skin.tga  tris.md2

./trunk/data1/models/weapons/g_machn:
tris.md2

./trunk/data1/models/weapons/g_rail:
tris.md2

./trunk/data1/models/weapons/g_rocket:
cover.md2  tris.md2

./trunk/data1/models/weapons/g_shotg:
tris.md2

./trunk/data1/models/weapons/g_shotg2:
tris.md2

./trunk/data1/models/weapons/v_bfg:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_blast:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_chain:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_hyperb:
cover.md2  skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_machn:
tris.md2

./trunk/data1/models/weapons/v_rail:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_rocket:
cover.md2  skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_shotg:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_shotg2:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_violator:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/particles:
aflash.tga     deathfield2.tga  reflect.tga      ripples.tga
basic.tga     deathfield.tga   r_explod_1.tga  sayicon.tga
beam.tga     dflash.tga      r_explod_2.tga  shell.tga
bflash.tga     explosion.tga      r_explod_3.tga  smoke_org.tga
blood.tga     flag.tga      r_explod_4.tga  smoke.tga
bubble.tga     flare.tga      r_explod_5.tga  voltage.tga
bullethole2.tga  leaderfield.tga  r_explod_6.tga  watersplash.tga
bullethole.tga     logo.tga      r_explod_7.tga
cflash.tga     puff.tga      ring.tga

./trunk/data1/pics:
a_bullets.tga        i_health.tga        num_5.tga
a_cells.tga        inventory.tga        num_6.tga
a_grenades.tga        i_score.tga            num_7.tga
anum_0.tga        i_team1.tga            num_8.tga
anum_1.tga        i_team2.tga            num_9.tga
anum_2.tga        m_bots.tga            num_minus.tga
anum_3.tga        m_controls.tga        options.tga
anum_4.tga        m_cursor0.tga        p_adrenaline.tga
anum_5.tga        m_dmoptions.tga        p_haste.tga
anum_6.tga        menu_back.jpg        p_invis.tga
anum_7.tga        m_joinserver.tga        p_invulnerability.tga
anum_8.tga        m_main_game_sel.tga     playerbox.tga
anum_9.tga        m_main_game.tga        p_powered.tga
anum_minus.tga        m_main_host_sel.tga     p_quad.tga
a_rockets.tga        m_main_host.tga        p_rewardpts.tga
a_shells.tga        m_main_join_sel.tga     p_sproing.tga
a_slugs.tga        m_main_join.tga        redplayerbox.tga
backtile.pcx        m_main_mont0.tga        rocketlauncher.tga
bar_background.tga  m_main_mont1.tga        sbfctf1.tga
bar_loading.tga     m_main_mont2.tga        sbfctf2.tga
beamgun.tga        m_main_mont3.tga        smartgun.tga
blaster.tga        m_main_mont4.tga        statbox.tga
blueplayerbox.tga   m_main_mont5.tga        strafer.tga
bomber.tga        m_main_options_sel.tga  tag1.tga
bots            m_main_options.tga        tag2.tga
ch1.tga            m_main_quit_sel.tga     team1.tga
ch2.tga            m_main_quit.tga        team2.tga
ch3.tga            m_main.tga            timer.tga
chaingun.tga        m_main_video_sel.tga    uparrow.tga
colormap.pcx        m_main_video.tga        vaporizor.tga
conback.tga        m_mouse_cursor.tga        violator.tga
conchars.tga        m_mutators.tga        w_bfg.tga
crosshairs        m_options.tga        w_blaster.tga
ctf1.tga        m_player.tga        w_chaingun.tga
ctf2.tga        m_quit.tga            w_glauncher.tga
disruptor.tga        m_single.tga        w_hyperblaster.tga
dnarrow.tga        m_startserver.tga        w_machinegun.tga
flamethrower.tga    m_video.tga            w_railgun.tga
grapple.tga        net.tga            w_rlauncher.tga
help.tga        num_0.tga            w_shotgun.tga
hover.tga        num_1.tga            w_sshotgun.tga
huds            num_2.tga            zoomscope1.tga
i_flag1.tga        num_3.tga            zoomscope2.tga
i_flag2.tga        num_4.tga            zoomscope3.tga

./trunk/data1/pics/bots:
enforcer  martiancyborg  martianenforcer

./trunk/data1/pics/bots/enforcer:
blue_i.jpg  default_i.jpg  red_i.jpg  stryker_i.jpg

./trunk/data1/pics/bots/martiancyborg:
blue_i.jpg  default_i.jpg  red_i.jpg

./trunk/data1/pics/bots/martianenforcer:
blue_i.jpg  default_i.jpg  gamara_i.jpg  red_i.jpg

./trunk/data1/pics/crosshairs:
alien2a.tga    hardcorech.tga     mechano.tga     robot.tga
alien2b.tga    havoc2.tga     ncool.tga     sniper.tga
alien2.tga     havoc3.tga     nile2.tga     sungod.tga
alien.tga      havoc.tga     nile3.tga     tech2.tga
chexcross.tga  intimidator2.tga  nile.tga     tech.tga
dot1.tga       intimidator3.tga  rage_cross.tga  transcircle.tga
freezy.tga     intimidator.tga     rgb.tga     vista.tga

./trunk/data1/pics/huds:
20061.tga     classic2.tga      gtv1.tga      retro2.tga
20062.tga     cleanblue1.tga   gtv2.tga      talon1.tga
20071.tga     cleanblue2.tga   marscreen1.tga  talon2.tga
20072.tga     cleangreen1.tga  marscreen2.tga  terminal-blue1.tga
8bit1.tga     cleangreen2.tga  mechanic1.tga   terminal-blue2.tga
8bit2.tga     cleanred1.tga      mechanic2.tga   terminal-green1.tga
alien1.tga     cleanred2.tga      nki_dark1.tga   terminal-green2.tga
alien2.tga     corpse1.tga      nki_dark2.tga   terminal-purple1.tga
alienblood1.tga  corpse2.tga      nki_darkb1.tga  terminal-purple2.tga
alienblood2.tga  cpu1.tga      nki_darkb2.tga  terminal-red1.tga
blood1.tga     cpu2.tga      oldskool1.tga   terminal-red2.tga
blood2.tga     freezy1.tga      oldskool2.tga   therock1.tga
classic1.tga     freezy2.tga      retro1.tga      therock2.tga

./trunk/data1/players:
commander  enforcer  lauren  martiancyborg  martianenforcer  slashbot

./trunk/data1/players/commander:
blue_i.jpg        drown1.wav       pain25_2.wav   w_chaingun.md2
blue.jpg        fall1.wav       pain50_1.wav   weapon.jpg
bump1.wav        fall2.wav       pain50_2.wav   weapon.md2
death1.wav        gurp1.wav       pain75_1.wav   w_hyperblaster.md2
death2.wav        gurp2.wav       pain75_2.wav   w_machinegun.md2
death3.wav        human       red_i.jpg      w_railgun.md2
death4.wav        jump1.wav       red.jpg      w_rlauncher.md2
default_i.jpg        pain100_1.wav  tris.md2      w_shotgun.md2
default.jpg        pain100_2.wav  w_bfg.md2      w_sshotgun.md2
default_normal.jpg  pain25_1.wav   w_blaster.md2  w_violator.md2

./trunk/data1/players/enforcer:
arm.md2            fall1.wav       pain25_1.wav   w_blaster.md2
blue_i.jpg        fall2.wav       pain25_2.wav   w_chaingun.md2
blue.jpg        gurp1.wav       pain50_1.wav   weapon.jpg
body.md2        gurp2.wav       pain50_2.wav   weapon.md2
bump1.wav        head.md2       pain75_1.wav   w_hyperblaster.md2
death1.wav        helmet.md2       pain75_2.wav   w_machinegun.md2
death2.wav        human       red_i.jpg      w_railgun.md2
death3.wav        jump1.wav       red.jpg      w_rlauncher.md2
death4.wav        leg.md2       stryker_i.jpg  w_shotgun.md2
default_i.jpg        lod1.md2       stryker.jpg      w_sshotgun.md2
default.jpg        lod2.md2       tris.md2      w_violator.md2
default_normal.tga  pain100_1.wav  usegibs
drown1.wav        pain100_2.wav  w_bfg.md2

./trunk/data1/players/lauren:
arm.md2            drown1.wav       pain25_2.wav    weapon.jpg
blue_i.jpg        fall1.wav       pain50_1.wav    weapon.md2
blue.jpg        fall2.wav       pain50_2.wav    w_hyperblaster.md2
body.md2        gurp1.wav       pain75_1.wav    w_machinegun.md2
bump1.wav        gurp2.wav       pain75_2.wav    w_railgun.md2
death1.wav        head.md2       red_i.jpg       w_rlauncher.md2
death2.wav        human       red.jpg       w_shotgun.md2
death3.wav        jump1.wav       tris.md2       w_sshotgun.md2
death4.wav        leg.md2       usegibs       w_violator.md2
default_i.jpg        pain100_1.wav  w_bfg.md2
default.jpg        pain100_2.wav  w_blaster.md2
default_normal.tga  pain25_1.wav   w_chaingun.md2

./trunk/data1/players/martiancyborg:
blue_i.jpg        fall1.wav       pain25_2.wav   w_chaingun.md2
blue.jpg        fall2.wav       pain50_1.wav   weapon.md2
bump1.wav        gurp1.wav       pain50_2.wav   weapon.tga
death1.wav        gurp2.wav       pain75_1.wav   w_hyperblaster.md2
death2.wav        helmet.md2       pain75_2.wav   w_machinegun.md2
death3.wav        jump1.wav       red_i.jpg      w_railgun.md2
death4.wav        lod1.md2       red.jpg      w_rlauncher.md2
default_i.jpg        lod2.md2       robot      w_shotgun.md2
default.jpg        pain100_1.wav  tris.md2      w_sshotgun.md2
default_normal.tga  pain100_2.wav  w_bfg.md2      w_violator.md2
drown1.wav        pain25_1.wav   w_blaster.md2

./trunk/data1/players/martianenforcer:
alien            drown1.wav      lod1.md2     usegibs
arm.md2            fall1.wav      lod2.md2     w_bfg.md2
blue_i.jpg        fall2.wav      pain100_1.wav  w_blaster.md2
blue.jpg        gamara_i.jpg  pain100_2.wav  w_chaingun.md2
body.md2        gamara.jpg      pain25_1.wav     weapon.md2
bump1.wav        gasp1.wav      pain25_2.wav     weapon.tga
death1.wav        gasp2.wav      pain50_1.wav     w_hyperblaster.md2
death2.wav        gurp1.wav      pain50_2.wav     w_machinegun.md2
death3.wav        gurp2.wav      pain75_1.wav     w_railgun.md2
death4.wav        head.md2      pain75_2.wav     w_rlauncher.md2
default_i.jpg        helmet.md2      red_i.jpg     w_shotgun.md2
default.jpg        jump1.wav      red.jpg     w_sshotgun.md2
default_normal.tga  leg.md2      tris.md2     w_violator.md2

./trunk/data1/players/slashbot:
blue_i.jpg        drown1.wav       pain50_1.wav   w_chaingun.md2
blue.jpg        fall1.wav       pain50_2.wav   weapon.jpg
bump1.wav        fall2.wav       pain75_1.wav   weapon.md2
death1.wav        gurp1.wav       pain75_2.wav   w_hyperblaster.md2
death2.wav        gurp2.wav       red_i.jpg      w_machinegun.md2
death3.wav        jump1.wav       red.jpg      w_railgun.md2
death4.wav        pain100_1.wav  robot      w_rlauncher.md2
default_i.jpg        pain100_2.wav  tris.md2      w_shotgun.md2
default.jpg        pain25_1.wav   w_bfg.md2      w_sshotgun.md2
default_normal.jpg  pain25_2.wav   w_blaster.md2  w_violator.md2

./trunk/data1/scripts:
caustics.rscript     fragment_shader.glsl        players.rscript
chrome.rscript         gunmen.rscript            textures.rscript
consoles.rscript     maps                vertex_shader.glsl
electrics2.rscript     menu.rscript            water1.arbf
electrics3.rscript     mesh_fragment_shader.glsl  water_fragment_shader.glsl
electrics.rscript     mesh_vertex_shader.glsl    water.rscript
fb_fragment_shader.glsl  models.rscript            water_vertex_shader.glsl
fb_vertex_shader.glsl     normals

./trunk/data1/scripts/maps:
aoa-atlantis.rscript    dm-aquous.rscript     dm-leviathan2k8.rscript
aoa-corrosion.rscript    dm-atlantis2k8.rscript     dm-leviathan.rscript
aoa-frost2k9.rscript    dm-babel.rscript     dm-liberation.rscript
aoa-morpheus.rscript    dm-beyond.rscript     dm-omega2k8.rscript
aoa-zorn.rscript    dm-bloodfactory.rscript  dm-saucer2k9.rscript
cp-grindery.rscript    dm-chasmatic2k9.rscript  dm-saucer.rscript
cp-ribeye.rscript    dm-chasmatic.rscript     dm-titan2k8.rscript
ctf-atlantis.rscript    dm-command2k9.rscript     dm-turbo2k8.rscript
ctf-chromium.rscript    dm-corrosion.rscript     dm-vesuvius.rscript
ctf-corrosion.rscript    dm-crucible2k8.rscript     dm-violator.rscript
ctf-cryogenic.rscript    dm-crucible.rscript     dm-warmachine2k9.rscript
ctf-europa2k8.rscript    dm-deimos2k9.rscript     dm-warmachine.rscript
ctf-frost2k9.rscript    dm-dismal2k8.rscript     dm-zion.rscript
ctf-icarus2.rscript    dm-dread.rscript     dm-zorn.rscript
ctf-stronghold.rscript    dm-dynamo2k8.rscript     tca-corrosion.rscript
ctf-terminal.rscript    dm-dynamo2.rscript     tca-cryogenic.rscript
ctf-titan2k8.rscript    dm-eternal.rscript     tca-europa2k8.rscript
ctf-vesuvius.rscript    dm-europa2k8.rscript     tca-frost.rscript
ctf-zorn.rscript    dm-furious2k8.rscript     tca-titan2k8.rscript
db-chromium.rscript    dm-grindery.rscript     tca-zion.rscript
db-icarus.rscript    dm-horus.rscript
db-vesuvius.rscript    dm-invasion.rscript

./trunk/data1/scripts/normals:
normals.rscript

./trunk/data1/sound:
doors  items  misc  music  player  smallmech  taunts  vehicles    weapons  world

./trunk/data1/sound/doors:
dr1_end.wav  dr1_mid.wav  dr1_strt.wav

./trunk/data1/sound/items:
damage2.wav   haste.wav     powerup.wav   protect.wav      sproing.wav
damage3.wav   l_health.wav  protect2.wav  respawn1.wav
damage.wav    m_health.wav  protect3.wav  s_health.wav
hasteout.wav  n_health.wav  protect4.wav  sproingout.wav

./trunk/data1/sound/misc:
1frags.wav        blue_scores.wav    menu2.wav       red_wins.wav
2frags.wav        bluevulnerable.wav    menu3.wav       reject.wav
3frags.wav        blue_wins_ctf.wav    one.wav           spawn1.wav
am_pkup.wav        blue_wins.wav    pc_up.wav       talk1.wav
ar1_pkup.wav        cow            rampage.wav       talk.wav
ar2_pkup.wav        db_pickup.wav    red_picked.wav       tele1.wav
ar3_pkup.wav        db_score.wav    redpndisabled.wav  tele_up.wav
bigtele.wav        fight.wav        redpnenabled.wav   three.wav
blue_picked.wav     godlike.wav        red_returned.wav   trigger1.wav
bluepndisabled.wav  hit.wav        red_scores.wav       two.wav
bluepnenabled.wav   lasfly.wav        redvulnerable.wav  w_pkup.wav
blue_returned.wav   menu1.wav        red_wins_ctf.wav

./trunk/data1/sound/misc/cow:
groan.wav  moo.wav  step1.wav

./trunk/data1/sound/music:
cp-ribeye.ogg  dm-eternal.ogg    dm-redred.ogg       menumusic.ogg
dm-deimos.ogg  dm-frontier.ogg    dm-saucer.ogg
dm-dismal.ogg  dm-horus.ogg    dm-turbo.ogg
dm-dynamo.ogg  dm-inferno.ogg    dm-warmachine.ogg

./trunk/data1/sound/player:
burn1.wav   fall1.wav  jump1.wav    male       step_metal1.wav    wade2.wav
burn2.wav   fall2.wav  land1.wav    step1.wav  step_metal2.wav    wade3.wav
death1.wav  fry.wav    lava1.wav    step2.wav  step_metal3.wav    watr_in.wav
death4.wav  gasp1.wav  lava2.wav    step3.wav  step_metal4.wav    watr_out.wav
drown1.wav  gasp2.wav  lava_in.wav  step4.wav  wade1.wav    watr_un.wav

./trunk/data1/sound/player/male:
bump1.wav   death4.wav    gurp1.wav      pain100_2.wav  pain50_2.wav
death1.wav  drown1.wav    gurp2.wav      pain25_1.wav   pain75_1.wav
death2.wav  fall1.wav    jump1.wav      pain25_2.wav   pain75_2.wav
death3.wav  fall2.wav    pain100_1.wav  pain50_1.wav

./trunk/data1/sound/smallmech:
sight.wav

./trunk/data1/sound/taunts:
commander  enforcer  lauren  martiancyborg  martianenforcer  slashbot

./trunk/data1/sound/taunts/commander:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/enforcer:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/lauren:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/martiancyborg:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/martianenforcer:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/slashbot:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/vehicles:
bomberidle.wav     flybomb.wav  shootbomb.wav   warning.wav
explodebomb.wav  got_in.wav   shootlaser.wav

./trunk/data1/sound/weapons:
biglaser.wav     grenlf1a.wav  machgf2b.wav  rocklr1b.wav
blastf1a.wav     grenlr1b.wav  machgf3b.wav  rocklx1a.wav
clank.wav     grenlx1a.wav  machgf4b.wav  shotgf1b.wav
clink01.wav     hypbrl1a.wav  machgf5b.wav  smartgun_hum.wav
clink02.wav     hyprbf1a.wav  noammo.wav    vaporizer_hum.wav
electroball.wav  lightoff.wav  railgf1a.wav  viofire1.wav
energyfield.wav  lighton.wav   rockfly.wav   viofire2.wav
grenlb1b.wav     machgf1b.wav  rocklf1a.wav  whoosh.wav

./trunk/data1/sound/world:
botwon.wav    electricity.wav  jumppad1.wav  ric1.wav    steam1.wav
button1.wav    explosion1.wav     laser1.wav    ric2.wav    steam2.wav
button2.wav    explosion2.wav     platstop.wav  ric3.wav    turbine1.wav
distantjet.wav    hyprbf1a.wav     rcktfly.wav   rocket.wav  youwin.wav

./trunk/data1/textures:
alien     arena5      common        metal        ramp1c.wal    ramp1f.wal
arena1     arena6      cr3blankclear.wal    null.tga    ramp1d.tga    ramp1.tga
arena10  arena7      dalek        rage        ramp1d.wal    ramp1.wal
arena2     arena8      evil        ramp1b.tga  ramp1e.tga    water
arena3     arena9      forsaken        ramp1b.wal  ramp1e.wal    xempx
arena4     billboards  martian        ramp1c.tga  ramp1f.tga

./trunk/data1/textures/alien:
support5.tga

./trunk/data1/textures/arena1:
jpad1a.tga  jpad1d.wal          metalbrick3c.tga    o3arch1.tga    o3bricks6.tga
jpad1a.wal  jpad1e.tga          metalbrick3d.tga    o3bricks12.tga    o3bricks.tga
jpad1b.tga  jpad1e.wal          metalbrick4a.tga    o3bricks21.tga    o3ice1.tga
jpad1b.wal  metalbrick1.tga   metalbrick4b.tga    o3bricks22.tga    o3ice2.tga
jpad1c.tga  metalbrick2.tga   metalbrick4c.tga    o3bricks23.tga    o3ice3.tga
jpad1c.wal  metalbrick3a.tga  metalbrick4d.tga    o3bricks2.tga    o3ice4.tga
jpad1d.tga  metalbrick3b.tga  metalbrick5.tga    o3bricks3.tga    o3rocks1.tga

./trunk/data1/textures/arena10:
bricks1_nm.tga      building6_nm.tga    container1.tga       pipes1.tga
bricks1.tga      building6.tga        container2_hm.tga  rockdirt1_hm.tga
bricks2_hm.tga      building7_nm.tga    container2_nm.tga  rockdirt1ng_hm.tga
bricks2_nm.tga      building7.tga        container2.tga       rockdirt1ng_nm.tga
bricks2.tga      building8_nm.tga    container3_hm.tga  rockdirt1ng.tga
bricks3.tga      building8.tga        container3_nm.tga  rockdirt1_nm.tga
building10.tga      building9_nm.tga    container3.tga       rockdirt1.tga
building1_nm.tga  building9.tga        container4_hm.tga  sewergrate1_nm.tga
building1.tga      cement1.tga        container4_nm.tga  sewergrate1.tga
building2_nm.tga  cobblestone_hm.tga    container4.tga       sign1.tga
building2.tga      cobblestoneng_hm.tga    heap1_nm.tga       sign2.tga
building3_nm.tga  cobblestoneng_nm.tga    heap1.tga       sign3.tga
building3.tga      cobblestoneng.tga    neonsign1.tga       sign4.tga
building4_nm.tga  cobblestone_nm.tga    neonsign2.tga       sign5.tga
building4.tga      cobblestone.tga    neonsign3.tga       sign6.tga
building5_nm.tga  container1_hm.tga    neonsign4.tga
building5.tga      container1_nm.tga    neonsign5.tga

./trunk/data1/textures/arena2:
grid2.tga  gridb.tga  gride.tga    metal1.tga  metal4.tga
grid3.tga  gridc.tga  lava_nm.tga  metal2.tga  metal5.tga
grida.tga  gridd.tga  lava.tga       metal3.tga  metal6.tga

./trunk/data1/textures/arena3:
acceleratora.tga  acceleratorf.wal  light1.tga    orbe.wal       wall1.tga
acceleratora.wal  acceleratorg.tga  light2.tga    orbf.tga       wall2.tga
acceleratorb.tga  acceleratorg.wal  orba.tga    orbf.wal       wall3.tga
acceleratorb.wal  ceiling1.tga        orba.wal    orbg.tga       wall4.tga
acceleratorc.tga  ceiling2.tga        orbb.tga    orbg.wal       wall5.tga
acceleratorc.wal  door1.tga        orbb.wal    orbh.tga       water_nm.tga
acceleratord.tga  floor1.tga        orbc.tga    orbh.wal       water.tga
acceleratord.wal  floor2_nm.tga     orbc.wal    trim1.tga
acceleratore.tga  floor2.tga        orbd.tga    trim2.tga
acceleratore.wal  floor3.tga        orbd.wal    trimlite1.tga
acceleratorf.tga  floor4.tga        orbe.tga    trimlite2.tga

./trunk/data1/textures/arena4:
bricks1_nm.tga    floor1.cpt     floor3_nm.tga  light3.tga       wall1_nm.tga
bricks1.tga    floor1_nm.tga  floor3.tga     support1_nm.tga  wall1.tga
comp1_nm.tga    floor1.tga     light1.tga     support1.tga     wall2_nm.tga
comp1.tga    floor2.tga     light2.tga     support2.tga     wall2.tga

./trunk/data1/textures/arena5:
bast1_nm.tga      egypt2.tga      light1.tga  lighte.tga      o3win12.tga
bast1.tga      egypt3.tga      light2.tga  lighte.wal      rock2_nm.tga
bast2.tga      egypt4.tga      lighta.tga  lightf.tga      rock2.tga
bricks4_1_nm.tga  egypt5.tga      lighta.wal  lightf.wal      rock_3b_nm.tga
bricks4_1.tga      egypt6_nm.tga   lightb.tga  o3cath11.tga    rock_3b.tga
cave_nm.tga      egypt6.tga      lightb.wal  o3cath3.tga     sekhmet3.tga
cave.tga      egypt7.tga      lightc.tga  o3cath5.tga     trim_nm.tga
chain.tga      fod.tga      lightc.wal  o3cath8.tga     trim_sm.tga
cobweb.tga      ground1_nm.tga  lightd.tga  o3rock5_nm.tga  trim.tga
egypt1.tga      ground1.tga      lightd.wal  o3rock5.tga

./trunk/data1/textures/arena6:
alienarena2.tga  ctfwinred.tga      icerock.tga     plate4.tga      skullite.tga
alienarena.tga     flamejet.tga      ice.tga     plate5_nm.tga      skull_nm.tga
blacktrans.tga     flare.tga      plate1_nm.tga  plate5_sm.tga      skull.tga
bricks1_hm.tga     fodblue.tga      plate1.tga     plate5.tga      snow_nm.tga
bricks1_nm.tga     girder1.tga      plate2_nm.tga  rimlight2.tga      snow.tga
bricks1_sm.tga     girder2.tga      plate2.tga     rimlight.tga      tech1.tga
bricks1.tga     icerock2_nm.tga  plate3_nm.tga  rings.tga      wires1.tga
city20.tga     icerock2.tga      plate3.tga     skullite_hm.tga
ctfwinblue.tga     icerock_nm.tga   plate4_nm.tga  skullite_nm.tga

./trunk/data1/textures/arena7:
bluegrid.tga   light1.tga     redgrid.tga    tekwall4.tga
ceiling1.tga   light2.tga     tekfloor1_nm.tga    tekwall5_nm.tga
floor1_hm.tga  light3.tga     tekfloor1.tga    tekwall5.tga
floor1_nm.tga  light4.tga     tekwall1_nm.tga    tekwall6_nm.tga
floor1.tga     light5.tga     tekwall1.tga    tekwall6.tga
floor2_hm.tga  light6.tga     tekwall2_nm.tga    tekwall7_nm.tga
floor2_nm.tga  light7.tga     tekwall2.tga    tekwall7.tga
floor2.tga     light8.tga     tekwall3_hm.tga    tekwall8_nm.tga
glass.tga      light9.tga     tekwall3_nm.tga    tekwall8.tga
grate1.tga     lightgid2.tga  tekwall3r_hm.tga    tekwall9_hm.tga
light10.tga    lightgid.tga   tekwall3r_nm.tga    tekwall9_nm.tga
light11.tga    metal1.tga     tekwall3r.tga    tekwall9.tga
light12.tga    metal2_nm.tga  tekwall3.tga    warning.tga
light13.tga    metal2.tga     tekwall4_nm.tga
light14.tga    metal3.tga     tekwall4r_nm.tga
light1r.tga    piston1.tga    tekwall4r.tga

./trunk/data1/textures/arena8:
bark1_hm.tga         crackedrock1.tga      floor3_hm.tga      metaltrim2_hm.tga
bark1_nm.tga         crackedrock2_hm.tga  floor3_nm.tga      metaltrim2_nm.tga
bark1.tga         crackedrock2_nm.tga  floor3.tga         metaltrim2.tga
barnroof_nm.tga      crackedrock2.tga      floor4_hm.tga      rock1_nm.tga
barnroof.tga         crackedrock3_hm.tga  floor4_nm.tga      rock1.tga
barnwindows.tga      crackedrock3_nm.tga  floor4.tga         roughwood_nm.tga
barnwood2_nm.TGA     crackedrock3.tga      grass2_nm.tga      roughwood.tga
barnwood2.tga         crackedrock4_hm.tga  grass2.tga         sand1.tga
barnwood_nm.tga      crackedrock4_nm.tga  grate1.tga         sand2.tga
barnwood.tga         crackedrock4.tga      ice.tga         slime_nm.tga
blackbrick1.tga      egyptbrick1_hm.tga   lavalmetal_nm.tga  slime.tga
blackbrick2.tga      egyptbrick1_nm.tga   lavalmetal.tga     snow_hm.tga
blackbrick3.tga      egyptbrick1.tga      leaves1.tga         snow_nm.tga
brickwall1_hm.tga    egyptfloor1_nm.tga   metal1_nm.tga      snow.tga
brickwall1_nm.tga    egyptfloor1.tga      metal1.tga         stonefloor1_hm.tga
brickwall1.tga         egyptrock1_hm.tga      metalroof_hm.tga   stonefloor1_nm.tga
cinderblocks_hm.tga  egyptrock1_nm.tga      metalroof_nm.tga   stonefloor1.tga
cinderblocks_nm.tga  egyptrock1.tga      metalroof.tga      wood1_hm.tga
cinderblocks.tga     egyptrock2_nm.tga      metaltrim1_hm.tga  wood1_nm.tga
crackedrock1_hm.tga  egyptrock2.tga      metaltrim1_nm.tga  wood1.tga
crackedrock1_nm.tga  fern.tga          metaltrim1.tga

./trunk/data1/textures/arena9:
beam_metal_nm.tga      icemetal1_nm.tga        panel3.tga
beam_metal.tga           icemetal1.tga           panel4_hm.tga
biggrate1_hm.tga       icemetal2_hm.tga        panel4_nm.tga
biggrate1_nm.tga       icemetal2_nm.tga        panel4.tga
biggrate1.tga           icemetal2.tga           panel5_nm.tga
boxmetal_hm.tga        iceplate_nm.tga           panel5.tga
boxmetal_nm.tga        iceplate.tga           platefloor1_hm.tga
boxmetal.tga           icetrim1_hm.tga           platefloor1_nm.tga
brokencement1_nm.tga   icetrim1_nm.tga           platefloor1.tga
brokencement1.tga      icetrim1.tga           platefloor2_hm.tga
cable1.tga           icetrim2_hm.tga           platefloor2_nm.tga
cable2.tga           icetrim2_nm.tga           platefloor2.tga
cable3.tga           icetrim2.tga           platefloor3_hm.tga
cable4.tga           icewall1_hm.tga           platefloor3_nm.tga
cementwall1_hm.tga     icewall1_nm.tga           platefloor3.tga
cementwall1_nm.tga     icewall1.tga           platefloor4_hm.tga
cementwall1.tga        icicles.tga           platefloor4_nm.tga
chainlinkfence.tga     lightwhite.tga           platefloor4.tga
circuitwall1_hm.jpg    metal1_nm.tga           platefloor5_hm.tga
circuitwall1_nm.jpg    metal1.tga           platefloor5_nm.tga
circuitwall1_nm.tga    metal2_nm.tga           platefloor5.tga
circuitwall1.tga       metal2.tga           platefloor6_hm.tga
comppanel2.tga           metal3_nm.tga           platefloor6_nm.tga
comppanel.tga           metal3.tga           platefloor6.tga
dmpltfloor1_hm.tga     metal4_nm.tga           platefloor7_hm.tga
dmpltfloor1_nm.tga     metal4.tga           platefloor7_nm.tga
dmpltfloor1.tga        metal5_nm.tga           platefloor7.tga
factorybricks1_hm.tga  metal5.tga           platefloor8_hm.tga
factorybricks1_nm.tga  metal6_nm.tga           platefloor8_nm.tga
factorybricks1_sm.tga  metal6.tga           platefloor8.tga
factorybricks1.tga     metalfloor1_hm.tga      redwall1_nm.tga
floor1_nm.tga           metalfloor1_nm.tga      redwall1.tga
floor1.tga           metalfloor1.tga           roundlight.tga
floor2_nm.tga           metalgrate1.tga           rustmetal1_nm.tga
floor2.tga           metalhole.tga           rustmetal1.tga
floor3_hm.tga           metalplate1_nm.tga      techfloor1_hm.tga
floor3_nm.tga           metalplate1.tga           techfloor1_nm.tga
floor3.tga           metalscale_hm.tga       techfloor1.tga
grate1_nm.tga           metalscale_nm.tga       techwall1_hm.tga
grate1.tga           metalscale.tga           techwall1_nm.tga
grate2.tga           metaltilefloor1_hm.tga  techwall1.tga
grate3.tga           metaltilefloor1_nm.tga  techwall2_hm.tga
greenfloor_nm.tga      metaltilefloor1.tga     techwall2_nm.tga
greenfloor.tga           metaltrim1.tga           techwall2.tga
greenglass.tga           metalwall1_hm.tga       techwall3_hm.tga
greenmetal_nm.tga      metalwall1_nm.tga       techwall3_nm.tga
greenmetal.tga           metalwall1.tga           techwall3.tga
greenwall1_nm.tga      metalwall2_hm.tga       trim1_nm.tga
greenwall1.tga           metalwall2_nm.tga       trim1.tga
greenwall2_hm.tga      metalwall2.tga           trim2_nm.tga
greenwall2_nm.tga      metalwall3_hm.tga       trim2.tga
greenwall2.tga           metalwall3_nm.tga       wall1_nm.tga
greenwall3_nm.tga      metalwall3.tga           wall1.tga
greenwall3.tga           metalwall4_hm.tga       wall2_hm.tga
greenwall4_nm.tga      metalwall4_nm.tga       wall2_nm.tga
greenwall4.tga           metalwall4.tga           wall2.tga
greenwall5_hm.jpg      metalwall5_hm.tga       weapongrate.tga
greenwall5_nm.tga      metalwall5_nm.tga       wetbricks1_hm.tga
greenwall5.tga           metalwall5.tga           wetbricks1_nm.tga
greenwall6_nm.tga      metalwall6_hm.tga       wetbricks1.tga
greenwall6.tga           metalwall6_nm.tga       wires1.tga
hexfloor1_hm.tga       metalwall6.tga           wires2.tga
hexfloor1_nm.tga       metalwall7_hm.tga       wires3.tga
hexfloor1.tga           metalwall7_nm.tga       wires4.tga
hexfloor2_hm.tga       metalwall7.tga           wires5.tga
hexfloor2_nm.tga       metalwall8_hm.tga       wires6.tga
hexfloor2.tga           metalwall8_nm.tga       wires7.tga
hexglass.tga           metalwall8.tga           wires8.tga
hexgratefloor_hm.tga   panel1_nm.tga           yellowmetal_nm.tga
hexgratefloor_nm.tga   panel1.tga           yellowmetal.tga
hexgratefloor.tga      panel2_nm.tga           yellowwall1_hm.jpg
icefloor1_nm.tga       panel2.tga           yellowwall1_nm.tga
icefloor1.tga           panel3_hm.tga           yellowwall1.tga
icemetal1_hm.tga       panel3_nm.tga

./trunk/data1/textures/billboards:
billboard1.tga    billboard2.tga    billboard3.tga    billboard4.tga

./trunk/data1/textures/common:
0_clip.tga    caulk.tga      hint.tga        nolightmap.tga    trigger.tga
0_hint.tga    clip.tga       missileclip.tga    origin.tga    weapclip.tga
0_sky1.tga    cushion.tga    nodraw.tga    qer_portal.tga    white.tga
areaportal.tga    full_clip.tga  nodrop.tga    slick.tga

./trunk/data1/textures/dalek:
column1.tga   floor2.tga  floor4.tga  wall2.tga  wall4.tga  wall6.tga
console1.tga  floor3.tga  wall1.tga   wall3.tga  wall5.tga  wall7.tga

./trunk/data1/textures/evil:
confllrtile2pad_nm.tga    e8warning_nm.tga       steptop_mtl2_nm.tga
confllrtile2pad.tga    e8warning.tga           steptop_mtl2.tga
drktek_symb_hm.tga    stepside_mtl2_hm.tga       steptop_mtl3_hm.tga
drktek_symb_nm.tga    stepside_mtl2_nm.tga       steptop_mtl3_nm.tga
drktek_symb.tga        stepside_mtl2.tga       steptop_mtl3.tga
e6basegrate_nm.tga    stepside_mtl3_hm.tga       techallmix_hm.tga
e6basegrate.tga        stepside_mtl3_nm.tga       techallmix_nm.tga
e6dtrimnd_nm.tga    stepside_mtl3.tga       techallmix.tga
e6dtrimnd.tga        stepside_mtl4light_hm.tga  trim_drkmtl_nm.tga
e6launchengine_hm.tga    stepside_mtl4light_nm.tga  trim_drkmtl.tga
e6launchengine_nm.tga    stepside_mtl4light.tga       trimrstmtlpipes_nm.tga
e6launchengine.tga    stepside_mtl5_nm.tga       trimrstmtlpipes.tga
e6supptrim128.tga    stepside_mtl5.tga       trstmtl_panelbig_hm.tga
e6trim_basic128_nm.tga    stepside_mtl_nm.tga       trstmtl_panelbig_nm.tga
e6trim_basic128.tga    stepside_mtl.tga       trstmtl_panelbig.tga
e8warning_hm.tga    steptop_mtl2_hm.tga

./trunk/data1/textures/forsaken:
glass.tga

./trunk/data1/textures/martian:
biometal1_hm.tga  glass1.tga     metal3.tga          shiphull_hm.tga
biometal1_nm.tga  grass.tga     metal4.tga          shiphull_nm.tga
biometal1.tga      grass_tga.tga  metal5.tga          shiphull.tga
chains.tga      light1.tga     metalrings1.tga      skytrees.tga
coiledwire.tga      light2.tga     metalrings2.tga      skytrees_tga.tga
console1.tga      light3.tga     ribtubeswirl_hm.jpg  tree2_tga.tga
console2.tga      light4.tga     ribtubeswirl_nm.jpg  tree_bottom.tga
console3.tga      light5.tga     ribtubeswirl.tga     tree_bottom_tga.tga
console4.tga      light6.tga     shiphull2_hm.tga     tree_tga.tga
floor1.tga      metal1.tga     shiphull2_nm.tga     tree_top.tga
floor2.tga      metal2.tga     shiphull2.tga          tree_top_tga.tga

./trunk/data1/textures/metal:
bigconduit.tga    light2_s.tga    metal2.tga    silo.tga      wall2.tga
ceiling1.tga    light2.tga    metal3.tga    smallconduit.tga  wall3.tga
door1.tga    light3_s.tga    metal4.tga    trim1.tga      wall4.tga
doorjam.tga    light3.tga    metal5.tga    trim2.tga      wall5.tga
fade1.tga    light4.tga    openfloor2.tga    wall1_nm.tga      wall6.tga
fade2.tga    light5_s.tga    openfloor.tga    wall1_sm.tga      walllite.tga
floor.tga    light5.tga    plat.tga    wall1.tga
light1_s.tga    medconduit.tga    saucer1.tga    wall2_nm.tga
light1.tga    metal1.tga    saucer2.tga    wall2_sm.tga

./trunk/data1/textures/rage:
beam_purple_hm.tga  hexfloor_hm.tga   metallight_2.tga
beam_purple_nm.tga  hexfloor_nm.tga   metal_panel.tga
beam_purple.tga     hexfloor_red.tga  rimlightpurple.tga
ceiling2_nm.tga     hexfloor.tga      support_beam.tga
ceiling2.tga        jpad1a.tga          support_column_hm.tga
ceiling_nm.tga        lava.tga          support_column_nm.tga
ceiling.tga        light10.tga       support_column.tga
floor2.tga        light12.tga       support_trim.tga
floor5.tga        light1.tga          trimlight_purple.tga
fod1.tga        light5.tga          trimlight_red.tga
grid1.tga        light7.tga          wall_blue.tga
hexfloor_blue.tga   light8.tga

./trunk/data1/textures/water:
bluewater_nm.tga  bluewater.tga  clearwater_nm.tga  clearwater.tga  waterpx.tga

./trunk/data1/textures/xempx:
a3light1b.tga  a7light10.wal  a7light2.tga  a9metal5.tga
a6bt.tga       a7light1b.tga  a7light3.tga  light1.tga
a7light10.tga  a7light1.tga   a7light4.tga  lightbeam1.tga

./trunk/data1/vehicles:
bomber    deathball  hover  strafer

./trunk/data1/vehicles/bomber:
bomb.md2  console_normal.tga  helmet.md2       skin.tga  v_wep.md2
bomb.tga  console.tga          skin_normal.tga  tris.md2  window.md2

./trunk/data1/vehicles/deathball:
deathball.md2  deathmask.tga    skin.tga
deathball.tga  skin_normal.tga    v_wep.md2

./trunk/data1/vehicles/hover:
console_normal.tga  flames.md2    skin_normal.tga  v_wep.md2
console.tga        skin.jpg    tris.md2     window.md2

./trunk/data1/vehicles/strafer:
console_normal.tga  skin_normal.tga  tris.md2    window.md2
console.tga        skin.tga         v_wep.md2

./trunk/docs:
AA\ Dutch.txt    AA\ German.txt       AA\ Italian.txt     AA\ Russian.txt
AA_ES.txt    AA\ Greek.txt       AA\ Polish.txt      license.txt
AA\ French.txt    AA\ Hungarian.txt  AA\ Portuguese.txt  README.txt

./trunk/source:
client         codered.sln     Makefile  ref_gl    unix
codered.dsp  codered.vcproj  null      release    utils3
codered.dsw  game         qcommon   server    win32

./trunk/source/client:
adivtab.h  cl_input.c  cl_tent.c  keys.h      qmenu.c        vid.h
anorms.h   cl_inv.c    cl_view.c  menu.c      qmenu.h        vid_menu.c
cl_cin.c   cl_main.c   console.c  mpg123.h    ref.h        x86.c
cl_ents.c  cl_newfx.c  console.h  mpglib.h    screen.h
cl_fx.c    cl_parse.c  curl      mpglib.lib  snd_file.c
cl_http.c  cl_pred.c   input.h      qal.c       snd_openal.c
client.h   cl_scrn.c   keys.c      qal.h       sound.h

./trunk/source/client/curl:
curl.h       easy.h    mprintf.h  stdcheaders.h
curlver.h  libcurl.lib    multi.h    types.h

./trunk/source/game:
acesrc      game.vcproj     g_items.c    g_spawn.c     g_weapon.c    p_weapon.c
c_cam.c   g_chase.c     g_local.h    g_svcmds.c    m_move.c    q_shared.c
cow.c      g_cmds.c     g_main.c     g_target.c    m_player.h    q_shared.h
cow.h      g_combat.c     g_misc.c     g_trigger.c   p_client.c
g_ai.c      g_ctf.c     g_monster.c  g_unlagged.c  p_hud.c
game.def  g_deathball.c  g_phys.c     g_utils.c     p_trail.c
game.h      g_func.c     g_save.c     g_vehicles.c  p_view.c

./trunk/source/game/acesrc:
acebot_ai.c       acebot_config.cpp  acebot_movement.c
acebot_cmds.c       acebot.h          acebot_nodes.c
acebot_compress.c  acebot_items.c     acebot_spawn.c

./trunk/source/null:
cl_null.c     in_null.c      swimp_null.c  vid_null.c
glimp_null.c  snddma_null.c  sys_null.c

./trunk/source/qcommon:
cmd.c      common.c  crc.h   files.c   net_chan.c  qcommon.h
cmodel.c  crc.c     cvar.c  mdfour.c  pmove.c      qfiles.h

./trunk/source/ref_gl:
anorms.h    r_draw.c   r_mapscript.cpp    r_model.h     r_varray.c
anormtab.h  r_image.c  r_math.c        r_postprocess.c  r_vlights.c
glext.h     r_image.h  r_math.h        r_script.c     r_warp.c
jpeg        r_light.c  r_mesh.c        r_script.h     vlights.h
qgl.h        r_local.h  r_misc.c        r_shadows.c     warpsin.h
r_bloom.c   r_main.c   r_model.c    r_surf.c

./trunk/source/ref_gl/jpeg:
jconfig.h  jmorecfg.h  jpeglib.h

./trunk/source/release:
arena  client  crded  ded  game  game.so  ref_gl

./trunk/source/release/arena:
acebot_ai.o       cow.o      g_func.o     g_svcmds.o    p_client.o
acebot_cmds.o       g_ai.o      g_items.o    g_target.o    p_hud.o
acebot_compress.o  game.so      g_main.o     g_trigger.o   p_trail.o
acebot_items.o       g_chase.o      g_misc.o     g_unlagged.o  p_view.o
acebot_movement.o  g_cmds.o      g_monster.o  g_utils.o     p_weapon.o
acebot_nodes.o       g_combat.o      g_phys.o     g_vehicles.o  q_shared.o
acebot_spawn.o       g_ctf.o      g_save.o     g_weapon.o
c_cam.o           g_deathball.o  g_spawn.o    m_move.o

./trunk/source/release/client:
cl_cin.o    cl_parse.o    console.o  net_chan.o  rw_unix.o     sv_send.o
cl_ents.o   cl_pred.o    crc.o       net_udp.o   snd_file.o    sv_user.o
cl_fx.o     cl_scrn.o    cvar.o       pmove.o     snd_openal.o  sv_world.o
cl_http.o   cl_tent.o    files.o    qal.o       sv_ccmds.o    sys_unix.o
cl_input.o  cl_view.o    glob.o       qal_unix.o  sv_ents.o     vid_menu.o
cl_inv.o    cmd.o    keys.o       qmenu.o     sv_game.o     vid_so.o
cl_main.o   cmodel.o    mdfour.o   q_shared.o  sv_init.o
cl_newfx.o  common.o    menu.o       q_shunix.o  sv_main.o

./trunk/source/release/ded:
cl_null.o  crc.o    mdfour.o    q_shared.o  sv_game.o  sv_user.o
cmd.o       cvar.o   net_chan.o    q_shunix.o  sv_init.o  sv_world.o
cmodel.o   files.o  net_udp.o    sv_ccmds.o  sv_main.o  sys_unix.o
common.o   glob.o   pmove.o    sv_ents.o   sv_send.o

./trunk/source/release/game:
acebot_ai.o       cow.o      g_items.o    g_target.o    p_hud.o
acebot_cmds.o       g_ai.o      g_main.o     g_trigger.o   p_trail.o
acebot_compress.o  g_chase.o      g_misc.o     g_unlagged.o  p_view.o
acebot_items.o       g_cmds.o      g_monster.o  g_utils.o     p_weapon.o
acebot_movement.o  g_combat.o      g_phys.o     g_vehicles.o  q_shared.o
acebot_nodes.o       g_ctf.o      g_save.o     g_weapon.o
acebot_spawn.o       g_deathball.o  g_spawn.o    m_move.o
c_cam.o           g_func.o      g_svcmds.o   p_client.o

./trunk/source/release/ref_gl:
gl_glx.o    r_draw.o   r_main.o  r_misc.o      r_script.o   r_varray.o
qgl_unix.o  r_image.o  r_math.o  r_model.o      r_shadows.o  r_vlights.o
r_bloom.o   r_light.o  r_mesh.o  r_postprocess.o  r_surf.o     r_warp.o

./trunk/source/server:
server.h    sv_ents.c  sv_init.c  sv_null.c  sv_user.c
sv_ccmds.c  sv_game.c  sv_main.c  sv_send.c  sv_world.c

./trunk/source/unix:
gl_glx.c  glob.h      net_udp.c   qasm.h      q_shunix.c  rw_unix.h   vid_so.c
glob.c      glw_unix.h  qal_unix.c  qgl_unix.c  rw_unix.c   sys_unix.c

./trunk/source/utils3:
bsp  common  Makefile

./trunk/source/utils3/bsp:
bsp.dsp  bsp.dsw  bspinfo3  bsp.ncb  bsp.opt  qbsp3  qrad3  qvis3

./trunk/source/utils3/bsp/bspinfo3:
bspinfo3.c  bspinfo3.dsp

./trunk/source/utils3/bsp/qbsp3:
brushbsp.c  glfile.c    portals.c  qbsp3.plg    textures.c
csg.c        leakfile.c    prtfile.c  qbsp.h    tree.c
faces.c     map.c    qbsp3.c    resource.h    writebsp.c
gldraw.c    nodraw.c    qbsp3.dsp  resource.rc

./trunk/source/utils3/bsp/qrad3:
lightmap.c  qrad3.c    qrad3.dsw  qrad.h
patches.c   qrad3.dsp  qrad3.plg  trace.c

./trunk/source/utils3/bsp/qvis3:
flow.c    qvis3.c  qvis3.dsp  qvis3.plg  qvis3_res.rc  resource.h  vis.h

./trunk/source/utils3/common:
bspfile.c  l3dslib.c  mathlib.c  memory.h    polylib.h     threads.c
bspfile.h  l3dslib.h  mathlib.h  parsecfg.c  qfiles.h     threads.h
cmdlib.c   lbmlib.c   md4.c     parsecfg.h  scriplib.c  trilib.c
cmdlib.h   lbmlib.h   memory.c     polylib.c   scriplib.h  trilib.h

./trunk/source/win32:
conproc.c  glw_win.h  net_wins.c  qal_win.c  resource.h  vid_dll.c
conproc.h  in_win.c   Q2.ico      qgl_win.c  snd_win.c     winquake.h
glw_imp.c  lib          q2.rc      q_shwin.c  sys_win.c

./trunk/source/win32/lib:
libjpeg.lib          libvorbis_static.lib    vorbisfile_static.lib
libogg_static.lib      ogg_static.lib    vorbis_static.lib
libvorbisfile_static.lib  vorbisenc_static.lib

./trunk/Tools:
aaradiant.exe  galaxy              Master\ Server  projects       web
defaults       LinuxScripts          prefabs          RubyBrowser  WinInstall
FUSE           Map\ compiling\ tools  PrefabScripts   statsgen

./trunk/Tools/defaults:
entities.def

./trunk/Tools/FUSE:
BUILDING.TXT  fuse.cbp      fuse.workspace      main.c     offline
config          fuse.exe      fuse.xcf          Makefile     slink.c
config.c      fuse.glade  global.h          models.c     slink.h
config.h      fuse.ico      iconv.dll          models.h
COPYING.TXT   fuse.rc      libglade-2.0-0.dll  NOTES.TXT

./trunk/Tools/FUSE/config:
games.xml

./trunk/Tools/FUSE/offline:
189.12.189.10-16574.udp  69.143.97.41-27920.udp
189.13.7.43-27910.udp     69.143.97.41-27970.udp
190.55.10.13-27910.udp     70.233.170.106-27910.udp
24.208.244.91-62753.udp  72.129.166.209-27910.udp
24.208.244.91-62754.udp  84.3.11.220-27910.udp
24.208.244.91-62755.udp  87.117.201.24-27920.udp
61.82.45.170-27910.udp     87.117.201.24-27930.udp
68.228.24.233-27910.udp  87.117.201.24-27940.udp
68.61.124.10-27930.udp     87.117.201.24-27950.udp
69.14.111.12-27910.udp     master2.corservers.com-27900.udp
69.143.97.41-27910.udp     master.corservers.com-27900.udp

./trunk/Tools/galaxy:
buddylist.db   Galaxy.dsw      PollServer.cpp           Socket.h
BuddyName.cpp  Galaxy.h          PollServer.h               Startup.cpp
BuddyName.h    Galaxy.plg      ReadMe.txt               Startup.h
fce32.dll      Galaxy.rc      res                   StdAfx.cpp
fce32.lib      hyperlink.cpp      resource.h               StdAfx.h
fce.h           hyperlink.h      SkinHeaderCtrl.cpp           UpdateDlg.cpp
Functions.cpp  keycode.h      SkinHeaderCtrl.h           UpdateDlg.h
Functions.h    MEMDC.H          SkinHorizontalScrollbar.cpp  UpdateGame.cpp
Galaxy.aps     mfcpp.cpp      SkinHorizontalScrollbar.h    userinfo.h
Galaxy.clw     mfcpp.h          SkinListCtrl.cpp           windebug.cpp
Galaxy.cpp     minmaxlogic.cpp      SkinListCtrl.h           windebug.h
GalaxyDlg.cpp  minmaxlogic.h      SkinVerticleScrollbar.cpp
GalaxyDlg.h    PlayerProfile.cpp  SkinVerticleScrollbar.h
Galaxy.dsp     PlayerProfile.h      Socket.cpp

./trunk/Tools/galaxy/res:
bitmap10.bmp  bitmap28.bmp             HorizontalScrollBarThumb.bmp
bitmap11.bmp  bitmap29.bmp             icon10.ico
bitmap12.bmp  bitmap2.bmp             icon11.ico
bitmap13.bmp  bitmap3.bmp             icon12.ico
bitmap14.bmp  bitmap4.bmp             icon1.ico
bitmap15.bmp  bitmap5.bmp             icon2.ico
bitmap16.bmp  bitmap6.bmp             icon3.ico
bitmap17.bmp  bitmap7.bmp             icon5.ico
bitmap18.bmp  bitmap8.bmp             icon6.ico
bitmap19.bmp  bitmap9.bmp             icon7.ico
bitmap1.bmp   ColumnHeaderEnd.bmp         ListCtrl_Tile.bmp
bitmap20.bmp  ColumnHeaderSpan.bmp         logo_big_02.bmp
bitmap21.bmp  ColumnHeaderStart.bmp         VerticleScrollbarBottom.bmp
bitmap22.bmp  computer.ico             VerticleScrollBarDownArrow.bmp
bitmap23.bmp  Galaxy.ico             VerticleScrollBarSpan.bmp
bitmap24.bmp  Galaxy.rc2             VerticleScrollBarThumb.bmp
bitmap25.bmp  HorizontalScrollBarLeftArrow.bmp     VerticleScrollbarTop.bmp
bitmap26.bmp  HorizontalScrollBarRightArrow.bmp  VerticleScrollBarUpArrow.bmp
bitmap27.bmp  HorizontalScrollBarSpan.bmp

./trunk/Tools/LinuxScripts:
check-configs  kill-runaway-crded  launchservers  rcon      svstat
check-master   launch-server       randomgravity  README

./trunk/Tools/Map compiling tools:
2007  2008

./trunk/Tools/Map compiling tools/2007:
qbsp3.exe  qrad3.exe  qvis3.exe

./trunk/Tools/Map compiling tools/2008:
qbsp3.exe  qrad3.exe  qvis3.exe

./trunk/Tools/Master Server:
CR\ Master.dsp    CR\ Master.dsw    crmaster.exe  master.c

./trunk/Tools/prefabs:
aasign.pfb       furnace.pfb    pillar2.pfb    skull.pfb     support9.pfb
archway1.pfb       hall1.pfb    pillar3.pfb    stairs.pfb    teleporter.pfb
beamchain.pfb       jramp.pfb    pillar.pfb     support1.pfb  wall1.pfb
blueflagpad.pfb    lamp1.pfb    pipe1.pfb      support2.pfb  wall2.pfb
computer1.pfb       light1.pfb    platform1.pfb  support3.pfb  walllite.pfb
computer2.pfb       light2.pfb    radar.pfb      support4.pfb  weaponpad.pfb
dbgoal.pfb       light3.pfb    ramp1.pfb      support5.pfb
door2.pfb       light4.pfb    sbend.pfb      support6.pfb
door.pfb       light5.pfb    shall.pfb      support7.pfb
floatingskull.pfb  light6.pfb    skullight.pfb  support8.pfb

./trunk/Tools/PrefabScripts:
pipegen.rb  torus.rb  wc_to_aa.rb

./trunk/Tools/projects:
alienarena.qe4

./trunk/Tools/RubyBrowser:
browser.glade  browser.png  browser.rbw  debug    INSTALL.TXT

./trunk/Tools/RubyBrowser/debug:
189.12.189.10-16574.dmp  69.143.97.41-27920.dmp
189.13.7.43-27910.dmp     69.143.97.41-27970.dmp
190.55.10.13-27910.dmp     70.233.170.106-27910.dmp
24.208.244.91-62753.dmp  72.129.166.209-27910.dmp
24.208.244.91-62754.dmp  84.3.11.220-27910.dmp
24.208.244.91-62755.dmp  87.117.201.24-27920.dmp
61.82.45.170-27910.dmp     87.117.201.24-27930.dmp
68.228.24.233-27910.dmp  87.117.201.24-27940.dmp
68.61.124.10-27930.dmp     87.117.201.24-27950.dmp
69.14.111.12-27910.dmp     master.corservers.com-27900.dmp
69.143.97.41-27910.dmp

./trunk/Tools/statsgen:
fce32.dll  keycode.h   statsgen.cpp  statsgen.ncb  statstemplate.html
fce32.lib  ReadMe.txt  statsgen.dsp  statsgen.opt  StdAfx.cpp
fce.h       StatsGen    statsgen.dsw  statsgen.plg  StdAfx.h

./trunk/Tools/statsgen/StatsGen:
about.html   clan3.html       clanrank.html  stats10.html  stats7.html
backup         clan4.html       clans.db         stats11.html  stats8.html
bestof.html  clan5.html       global.html    stats1.html   stats9.html
clan0.html   clan6.html       index.html     stats2.html   statsgen.exe
clan10.html  clan7.html       menu.html      stats3.html   top.html
clan11.html  clan8.html       playerrank.db  stats4.html
clan1.html   clan9.html       poll.db         stats5.html
clan2.html   clanladder.html  sorted.db      stats6.html

./trunk/Tools/statsgen/StatsGen/backup:

./trunk/Tools/web:
adcode.txt  COPYING      INSTALL.TXT  rss        style.css
browser     dmflags.html  live           scan
config.php  index.html      remote.php   stats.mysql

./trunk/Tools/web/browser:
flags       healthcheck-master2.php  index.php  maps.php        servers.php
flags.php  healthcheck.php        ip_files   players.php    statfuncs.php
graph.php  img                maps       searchfuncs.php    support.php

./trunk/Tools/web/browser/flags:
A1.gif    BJ.gif    CZ.gif    GL.gif    JP.gif    MH.gif        NR.gif  SI.gif  UM.gif
A2.gif    BM.gif    DE.gif    GM.gif    KE.gif    MK.gif        NU.gif  SK.gif  US.gif
AD.gif    BN.gif    DJ.gif    GN.gif    KG.gif    ML.gif        NZ.gif  SL.gif  UY.gif
AE.gif    BO.gif    DK.gif    GP.gif    KH.gif    MM.gif        OM.gif  SM.gif  UZ.gif
AF.gif    BR.gif    DM.gif    GQ.gif    KI.gif    MN.gif        PA.gif  SN.gif  VA.gif
AG.gif    BS.gif    DO.gif    GR.gif    KM.gif    MO.gif        PE.gif  SO.gif  VC.gif
AI.gif    BT.gif    DZ.gif    GT.gif    KN.gif    MP.gif        PF.gif  SR.gif  VE.gif
AL.gif    BV.gif    EC.gif    GU.gif    KP.gif    MQ.gif        PG.gif  ST.gif  VG.gif
AM.gif    BW.gif    EE.gif    GW.gif    KR.gif    MR.gif        PH.gif  SV.gif  VI.gif
AN.gif    BY.gif    EG.gif    GY.gif    KW.gif    MS.gif        PK.gif  SY.gif  VN.gif
AO.gif    BZ.gif    ER.gif    HK.gif    KY.gif    MT.gif        PL.gif  SZ.gif  VU.gif
AP.gif    CA.gif    ES.gif    HM.gif    KZ.gif    MU.gif        PR.gif  TC.gif  WF.gif
AQ.gif    CD.gif    ET.gif    HN.gif    LA.gif    MV.gif        PS.gif  TD.gif  WS.gif
AR.gif    CF.gif    EU.gif    HR.gif    LB.gif    MW.gif        PT.gif  TG.gif  YE.gif
AS.gif    CG.gif    FI.gif    HT.gif    LC.gif    MX.gif        PW.gif  TH.gif  YT.gif
AT.gif    CH.gif    FJ.gif    HU.gif    LI.gif    MY.gif        PY.gif  TJ.gif  YU.gif
AU.gif    CI.gif    FK.gif    ID.gif    LK.gif    MZ.gif        QA.gif  TK.gif  ZA.gif
AW.gif    CK.gif    FM.gif    IE.gif    LR.gif    NA.gif        RE.gif  TM.gif  ZM.gif
AZ.gif    CL.gif    FO.gif    IL.gif    LS.gif    NC.gif        RO.gif  TN.gif  ZW.gif
BA.gif    CM.gif    FR.gif    IN.gif    LT.gif    NE.gif        RU.gif  TO.gif  ZZ.gif
BB.gif    CN.gif    GA.gif    IO.gif    LU.gif    NF.gif        RW.gif  TR.gif
BD.gif    CO.gif    GB.gif    IQ.gif    LV.gif    NG.gif        SA.gif  TT.gif
BE.gif    CR.gif    GD.gif    IR.gif    LY.gif    NI.gif        SB.gif  TV.gif
BF.gif    CS.gif    GE.gif    IS.gif    MA.gif    NL.gif        SC.gif  TW.gif
BG.gif    CU.gif    GF.gif    IT.gif    MC.gif    noflag.gif  SD.gif  TZ.gif
BH.gif    CV.gif    GH.gif    JM.gif    MD.gif    NO.gif        SE.gif  UA.gif
BI.gif    CY.gif    GI.gif    JO.gif    MG.gif    NP.gif        SG.gif  UG.gif

./trunk/Tools/web/browser/img:
down.gif             server_browser_cooldark_src.jpg  [www.gif](www.gif)
server_browser_cooldark.jpg  up.gif

./trunk/Tools/web/browser/ip_files:
0.php     12.php   15.php   18.php   219.php  249.php  48.php  78.php
100.php  130.php  160.php  190.php  21.php   24.php   49.php  79.php
101.php  131.php  161.php  191.php  220.php  250.php  4.php   7.php
102.php  132.php  162.php  192.php  221.php  251.php  50.php  80.php
103.php  133.php  163.php  193.php  222.php  252.php  51.php  81.php
104.php  134.php  164.php  194.php  223.php  253.php  52.php  82.php
105.php  135.php  165.php  195.php  224.php  254.php  53.php  83.php
106.php  136.php  166.php  196.php  225.php  255.php  54.php  84.php
107.php  137.php  167.php  197.php  226.php  25.php   55.php  85.php
108.php  138.php  168.php  198.php  227.php  26.php   56.php  86.php
109.php  139.php  169.php  199.php  228.php  27.php   57.php  87.php
10.php     13.php   16.php   19.php   229.php  28.php   58.php  88.php
110.php  140.php  170.php  1.php    22.php   29.php   59.php  89.php
111.php  141.php  171.php  200.php  230.php  2.php    5.php   8.php
112.php  142.php  172.php  201.php  231.php  30.php   60.php  90.php
113.php  143.php  173.php  202.php  232.php  31.php   61.php  91.php
114.php  144.php  174.php  203.php  233.php  32.php   62.php  92.php
115.php  145.php  175.php  204.php  234.php  33.php   63.php  93.php
116.php  146.php  176.php  205.php  235.php  34.php   64.php  94.php
117.php  147.php  177.php  206.php  236.php  35.php   65.php  95.php
118.php  148.php  178.php  207.php  237.php  36.php   66.php  96.php
119.php  149.php  179.php  208.php  238.php  37.php   67.php  97.php
11.php     14.php   17.php   209.php  239.php  38.php   68.php  98.php
120.php  150.php  180.php  20.php   23.php   39.php   69.php  99.php
121.php  151.php  181.php  210.php  240.php  3.php    6.php   9.php
122.php  152.php  182.php  211.php  241.php  40.php   70.php  countries.php
123.php  153.php  183.php  212.php  242.php  41.php   71.php  readme.txt
124.php  154.php  184.php  213.php  243.php  42.php   72.php  sources.txt
125.php  155.php  185.php  214.php  244.php  43.php   73.php  unknown.php
126.php  156.php  186.php  215.php  245.php  44.php   74.php
127.php  157.php  187.php  216.php  246.php  45.php   75.php
128.php  158.php  188.php  217.php  247.php  46.php   76.php
129.php  159.php  189.php  218.php  248.php  47.php   77.php

./trunk/Tools/web/browser/maps:
1st  3rd  default_341x256.jpg  default_80x60.jpg

./trunk/Tools/web/browser/maps/1st:
aoa-atlantis_341x256.jpg     dm-crucible2k8_341x256.jpg
aoa-atlantis_80x60.jpg         dm-crucible2k8_80x60.jpg
aoa-corrosion_341x256.jpg    dm-crucible_341x256.jpg
aoa-corrosion_80x60.jpg      dm-crucible_80x60.jpg
aoa-frost_341x256.jpg         dm-deimos2k9_341x256.jpg
aoa-frost_80x60.jpg         dm-deimos2k9_80x60.jpg
aoa-morpheus_341x256.jpg     dm-dismal2k8_341x256.jpg
aoa-morpheus_80x60.jpg         dm-dismal2k8_80x60.jpg
aoa-zorn_341x256.jpg         dm-dread_341x256.jpg
aoa-zorn_80x60.jpg         dm-dread_80x60.jpg
cp-grindery_341x256.jpg      dm-dynamo2k8_341x256.jpg
cp-grindery_80x60.jpg         dm-dynamo2k8_80x60.jpg
cp-ribeye_341x256.jpg         dm-eternal_341x256.jpg
cp-ribeye_80x60.jpg         dm-eternal_80x60.jpg
ctf-atlantis_341x256.jpg     dm-europa2k8_341x256.jpg
ctf-atlantis_80x60.jpg         dm-europa2k8_80x60.jpg
ctf-chromium_341x256.jpg     dm-furious2k8_341x256.jpg
ctf-chromium_80x60.jpg         dm-furious2k8_80x60.jpg
ctf-corrosion_341x256.jpg    dm-horus_341x256.jpg
ctf-corrosion_80x60.jpg      dm-horus_80x60.jpg
ctf-cryogenic_341x256.jpg    dm-leviathan2k8_341x256.jpg
ctf-cryogenic_80x60.jpg      dm-leviathan2k8_80x60.jpg
ctf-europa2k8_341x256.jpg    dm-liberation_341x256.jpg
ctf-europa2k8_80x60.jpg      dm-liberation_80x60.jpg
ctf-frost_341x256.jpg         dm-omega2k8_341x256.jpg
ctf-frost_80x60.jpg         dm-omega2k8_80x60.jpg
ctf-icarus2_341x256.jpg      dm-omega_341x256.jpg
ctf-icarus2_80x60.jpg         dm-omega_80x60.jpg
ctf-titan2k8_341x256.jpg     dm-saucer_341x256.jpg
ctf-titan2k8_80x60.jpg         dm-saucer_80x60.jpg
ctf-vesuvius_341x256.jpg     dm-titan2k8_341x256.jpg
ctf-vesuvius_80x60.jpg         dm-titan2k8_80x60.jpg
ctf-zorn_341x256.jpg         dm-turbo2k8_341x256.jpg
ctf-zorn_80x60.jpg         dm-turbo2k8_80x60.jpg
db-chromium_341x256.jpg      dm-vesuvius_341x256.jpg
db-chromium_80x60.jpg         dm-vesuvius_80x60.jpg
db-icarus_341x256.jpg         dm-violator_341x256.jpg
db-icarus_80x60.jpg         dm-violator_80x60.jpg
db-vesuvius_341x256.jpg      dm-warmachine_341x256.jpg
db-vesuvius_80x60.jpg         dm-warmachine_80x60.jpg
dm-aquous_341x256.jpg         dm-zion_341x256.jpg
dm-aquous_80x60.jpg         dm-zion_80x60.jpg
dm-atlantis2k8_341x256.jpg   dm-zorn_341x256.jpg
dm-atlantis2k8_80x60.jpg     dm-zorn_80x60.jpg
dm-babel_341x256.jpg         tca-corrosion_341x256.jpg
dm-babel_80x60.jpg         tca-corrosion_80x60.jpg
dm-beyond_341x256.jpg         tca-cryogenic_341x256.jpg
dm-beyond_80x60.jpg         tca-cryogenic_80x60.jpg
dm-bloodfactory_341x256.jpg  tca-europa2k8_341x256.jpg
dm-bloodfactory_80x60.jpg    tca-europa2k8_80x60.jpg
dm-chasmatic_341x256.jpg     tca-frost_341x256.jpg
dm-chasmatic_80x60.jpg         tca-frost_80x60.jpg
dm-command_341x256.jpg         tca-titan2k8_341x256.jpg
dm-command_80x60.jpg         tca-titan2k8_80x60.jpg
dm-corrosion_341x256.jpg     tca-zion_341x256.jpg
dm-corrosion_80x60.jpg         tca-zion_80x60.jpg

./trunk/Tools/web/browser/maps/3rd:
ahtcity-aoa_341x256.jpg        dm-dynamo2_341x256.jpg
ahtcity-aoa_80x60.jpg        dm-dynamo2_80x60.jpg
ahtcity-ctf_341x256.jpg        dm-dynamo_341x256.jpg
ahtcity-ctf_80x60.jpg        dm-dynamo_80x60.jpg
ahtcity-dm_341x256.jpg        dm-egyptian_341x256.jpg
ahtcity-dm_80x60.jpg        dm-egyptian_80x60.jpg
aoa1_341x256.jpg        dm-electro_341x256.jpg
aoa1_80x60.jpg            dm-electro_80x60.jpg
aoa2_341x256.jpg        dm-europa_341x256.jpg
aoa2_80x60.jpg            dm-europa_80x60.jpg
aoa-ahtcity_341x256.jpg        dm-fortofpillars_341x256.jpg
aoa-ahtcity_80x60.jpg        dm-fortofpillars_80x60.jpg
aoa-aztec_341x256.jpg        dm-frontier2_341x256.jpg
aoa-aztec_80x60.jpg        dm-frontier2_80x60.jpg
aoa-aztec-dark_341x256.jpg    dm-frontier_341x256.jpg
aoa-aztec-dark_80x60.jpg    dm-frontier_80x60.jpg
aoa-carnage_341x256.jpg        dm-furious_341x256.jpg
aoa-carnage_80x60.jpg        dm-furious_80x60.jpg
aoa-infinity_run_341x256.jpg    dm-gauntlet_341x256.jpg
aoa-infinity_run_80x60.jpg    dm-gauntlet_80x60.jpg
aoa-killbox_341x256.jpg        dm-grindery_341x256.jpg
aoa-killbox_80x60.jpg        dm-grindery_80x60.jpg
aoa-magma_341x256.jpg        dm-hungary_341x256.jpg
aoa-magma_80x60.jpg        dm-hungary_80x60.jpg
aoa-meatgrinder_341x256.jpg    dm-hypercube_341x256.jpg
aoa-meatgrinder_80x60.jpg    dm-hypercube_80x60.jpg
aoa-meatgrinder-x2_341x256.jpg    dm-inferno_341x256.jpg
aoa-meatgrinder-x2_80x60.jpg    dm-inferno_80x60.jpg
aoa-mgcity_341x256.jpg        dm-infinib_341x256.jpg
aoa-mgcity_80x60.jpg        dm-infinib_80x60.jpg
aoa-obsidian_341x256.jpg    dm-infinic_341x256.jpg
aoa-obsidian_80x60.jpg        dm-infinic_80x60.jpg
aoa-q3dm17_341x256.jpg        dm-infinity_341x256.jpg
aoa-q3dm17_80x60.jpg        dm-infinity_80x60.jpg
aoa-signs-day_341x256.jpg    dmintro_341x256.jpg
aoa-signs-day_80x60.jpg        dmintro_80x60.jpg
aoa-signs-fog_341x256.jpg    dm-khanate_341x256.jpg
aoa-signs-fog_80x60.jpg        dm-khanate_80x60.jpg
aoa-signs-night_341x256.jpg    dm-killbox_341x256.jpg
aoa-signs-night_80x60.jpg    dm-killbox_80x60.jpg
aoa-tourney0_341x256.jpg    dm-leviathan_341x256.jpg
aoa-tourney0_80x60.jpg        dm-leviathan_80x60.jpg
ctf0_341x256.jpg        dm-magma_341x256.jpg
ctf0_80x60.jpg            dm-magma_80x60.jpg
ctf1_341x256.jpg        dm-martianfactory_341x256.jpg
ctf1_80x60.jpg            dm-martianfactory_80x60.jpg
ctf2_341x256.jpg        dm-maya_341x256.jpg
ctf2_80x60.jpg            dm-maya_80x60.jpg
ctf-2fortx_341x256.jpg        dm-meatgrinder_341x256.jpg
ctf-2fortx_80x60.jpg        dm-meatgrinder_80x60.jpg
ctf3_341x256.jpg        dm-meatgrinder-x2_341x256.jpg
ctf3_80x60.jpg            dm-meatgrinder-x2_80x60.jpg
ctf-ahtcity_341x256.jpg        dm-merterprizon_341x256.jpg
ctf-ahtcity_80x60.jpg        dm-merterprizon_80x60.jpg
ctf-blood_341x256.jpg        dm-mgcity2-beta_341x256.jpg
ctf-blood_80x60.jpg        dm-mgcity2-beta_80x60.jpg
ctf-europa_341x256.jpg        dm-mgcity_341x256.jpg
ctf-europa_80x60.jpg        dm-mgcity_80x60.jpg
ctf-fortofpillars_341x256.jpg    dm-module_341x256.jpg
ctf-fortofpillars_80x60.jpg    dm-module_80x60.jpg
ctf-icarus_341x256.jpg        dm-mp1m10_341x256.jpg
ctf-icarus_80x60.jpg        dm-mp1m10_80x60.jpg
ctf-killbox_341x256.jpg        dm-negator_341x256.jpg
ctf-killbox_80x60.jpg        dm-negator_80x60.jpg
ctf-magma_341x256.jpg        dm-nkitrn1_341x256.jpg
ctf-magma_80x60.jpg        dm-nkitrn1_80x60.jpg
ctf-meatgrinder-x2_341x256.jpg    dm-obsidian2_341x256.jpg
ctf-meatgrinder-x2_80x60.jpg    dm-obsidian2_80x60.jpg
ctf-mgcity_341x256.jpg        dm-obsidian_341x256.jpg
ctf-mgcity_80x60.jpg        dm-obsidian_80x60.jpg
ctf-rockwar_341x256.jpg        dm-outpost_341x256.jpg
ctf-rockwar_80x60.jpg        dm-outpost_80x60.jpg
ctf-spacejam_341x256.jpg    dm-probe_341x256.jpg
ctf-spacejam_80x60.jpg        dm-probe_80x60.jpg
ctf-stronghold_341x256.jpg    dm-q1dm4_341x256.jpg
ctf-stronghold_80x60.jpg    dm-q1dm4_80x60.jpg
ctf-terminal_341x256.jpg    dm-q1dm6_341x256.jpg
ctf-terminal_80x60.jpg        dm-q1dm6_80x60.jpg
ctf-titan_341x256.jpg        dm-q3dm17_341x256.jpg
ctf-titan_80x60.jpg        dm-q3dm17_80x60.jpg
db-egyptian_341x256.jpg        dm-quakepanic_341x256.jpg
db-egyptian_80x60.jpg        dm-quakepanic_80x60.jpg
db-electro_341x256.jpg        dm-reactor4_341x256.jpg
db-electro_80x60.jpg        dm-reactor4_80x60.jpg
db-europa_341x256.jpg        dm-redred_341x256.jpg
db-europa_80x60.jpg        dm-redred_80x60.jpg
db-frontier_341x256.jpg        dm-rockasm_341x256.jpg
db-frontier_80x60.jpg        dm-rockasm_80x60.jpg
db-inferno_341x256.jpg        dm-signs-day_341x256.jpg
db-inferno_80x60.jpg        dm-signs-day_80x60.jpg
db-infinity_341x256.jpg        dm-signs-fog_341x256.jpg
db-infinity_80x60.jpg        dm-signs-fog_80x60.jpg
db-killbox_341x256.jpg        dm-signs-night_341x256.jpg
db-killbox_80x60.jpg        dm-signs-night_80x60.jpg
db-magma_341x256.jpg        dm-sin-khanate_341x256.jpg
db-magma_80x60.jpg        dm-sin-khanate_80x60.jpg
db-meatgrinder_341x256.jpg    dm-tangle_341x256.jpg
db-meatgrinder_80x60.jpg    dm-tangle_80x60.jpg
db-meatgrinder-x2_341x256.jpg    dm-titan_341x256.jpg
db-meatgrinder-x2_80x60.jpg    dm-titan_80x60.jpg
db-obsidian_341x256.jpg        dm-turbo_341x256.jpg
db-obsidian_80x60.jpg        dm-turbo_80x60.jpg
db-q3dm17_341x256.jpg        dm-ufc2-moth_341x256.jpg
db-q3dm17_80x60.jpg        dm-ufc2-moth_80x60.jpg
db-stronghold_341x256.jpg    dm-ufc_341x256.jpg
db-stronghold_80x60.jpg        dm-ufc_80x60.jpg
dm0_341x256.jpg            mgcity-aoa_341x256.jpg
dm0_80x60.jpg            mgcity-aoa_80x60.jpg
dm10_341x256.jpg        mgcity-ctf_341x256.jpg
dm10_80x60.jpg            mgcity-ctf_80x60.jpg
dm11_341x256.jpg        mgcity-dm_341x256.jpg
dm11_80x60.jpg            mgcity-dm_80x60.jpg
dm12a_341x256.jpg        q3dm18_341x256.jpg
dm12a_80x60.jpg            q3dm18_80x60.jpg
dm1_341x256.jpg            quakepanic01_341x256.jpg
dm1_80x60.jpg            quakepanic01_80x60.jpg
dm2_341x256.jpg            restplace_341x256.jpg
dm2_80x60.jpg            restplace_80x60.jpg
dm3_341x256.jpg            rockasm_341x256.jpg
dm3_80x60.jpg            rockasm_80x60.jpg
dm4_341x256.jpg            rockwar-ctf_341x256.jpg
dm4_80x60.jpg            rockwar-ctf_80x60.jpg
dm5_341x256.jpg            tca-europa_341x256.jpg
dm5_80x60.jpg            tca-europa_80x60.jpg
dm6_341x256.jpg            tca-europa-aoa_341x256.jpg
dm6_80x60.jpg            tca-europa-aoa_80x60.jpg
dm7_341x256.jpg            tca-killbox_341x256.jpg
dm7_80x60.jpg            tca-killbox_80x60.jpg
dm8_341x256.jpg            tca-killbox-aoa_341x256.jpg
dm8_80x60.jpg            tca-killbox-aoa_80x60.jpg
dm-ahtcity_341x256.jpg        tca-magma_341x256.jpg
dm-ahtcity_80x60.jpg        tca-magma_80x60.jpg
dm-area51_341x256.jpg        tca-meatgrinder-x2_341x256.jpg
dm-area51_80x60.jpg        tca-meatgrinder-x2_80x60.jpg
dm-atlantis_341x256.jpg        tca-meatgrinder-x2-a_341x256.jpg
dm-atlantis_80x60.jpg        tca-meatgrinder-x2-a_80x60.jpg
dm-aztec_341x256.jpg        tca-meatgrinder-x2-aoa_341x256.jpg
dm-aztec_80x60.jpg        tca-meatgrinder-x2-aoa_80x60.jpg
dm-aztec-dark_341x256.jpg    tca-module_341x256.jpg
dm-aztec-dark_80x60.jpg        tca-module_80x60.jpg
dm-aztec-matrix_341x256.jpg    tca-q3dm17_341x256.jpg
dm-aztec-matrix_80x60.jpg    tca-q3dm17_80x60.jpg
dm-blood_341x256.jpg        tca-q3dm17-aoa_341x256.jpg
dm-blood_80x60.jpg        tca-q3dm17-aoa_80x60.jpg
dm-bounce_341x256.jpg        tca-spacejam_341x256.jpg
dm-bounce_80x60.jpg        tca-spacejam_80x60.jpg
dm-catfight_341x256.jpg        tca-spacejam-aoa_341x256.jpg
dm-catfight_80x60.jpg        tca-spacejam-aoa_80x60.jpg
dm-cavern_341x256.jpg        tca-stronghold_341x256.jpg
dm-cavern_80x60.jpg        tca-stronghold_80x60.jpg
dm-chthon_341x256.jpg        tca-terminal-aoa_341x256.jpg
dm-chthon_80x60.jpg        tca-terminal-aoa_80x60.jpg
dm-deathbox_341x256.jpg        tca-titan_341x256.jpg
dm-deathbox_80x60.jpg        tca-titan_80x60.jpg
dm-deimos_341x256.jpg        tourney0_341x256.jpg
dm-deimos_80x60.jpg        tourney0_80x60.jpg
dm-dismal_341x256.jpg        tourney1_341x256.jpg
dm-dismal_80x60.jpg        tourney1_80x60.jpg
dm-dune_341x256.jpg        tourney2_341x256.jpg
dm-dune_80x60.jpg        tourney2_80x60.jpg
dm-dungeon_341x256.jpg        tourney3_341x256.jpg
dm-dungeon_80x60.jpg        tourney3_80x60.jpg

./trunk/Tools/web/live:
aabanner.jpg  config.php  COPYING  font  index.html  live.php

./trunk/Tools/web/live/font:
NEUROPOL.TTF  READ_ME.TXT

./trunk/Tools/web/rss:
rss.php

./trunk/Tools/web/scan:
index.html  scan.php

./trunk/Tools/WinInstall:
alienarena2007.iss


[/SIZE]

---

### Post by KinKiac on 2009-08-08
> **AxelMan0 said:**
> There is a makefile and a whole bunch of .exe and .dlls as if I had downloaded the windows version. There is a file called check-configs in the "linux scripts" directory but it appears to only relate to server info. The readme contains only install information and there is a file called "game.so" in the "data1" directory. I used this command to get it from subversion:

     svn co [SIZE=2]svn://svn.icculus.org/alienarena/trunk

Here is the extremely long list of files from dir -R, sorry about this but thank god for ctrl+f haha. It's too big to attatch it :(.
```

.:
directory  trunk

./trunk:
Aa1.ico  botconfigurator.exe  crx.exe  fce16.dll   libcurl.dll    Tools
aa.png     botinfo          data1    fce32.dll   oalinst.exe    zlib1.dll
arena     crded              docs     Galaxy.exe  source

./trunk/arena:
default.cfg  game.so  maps.lst    motd.txt  pics    server.cfg

./trunk/arena/pics:

./trunk/botinfo:
^3Marty.cfg         dm-chasmatic.tmp      dm-warmachine2k9.tmp
allbots.tmp         dm-command2k9.tmp      dm-warmachine.tmp
aoa-atlantis.tmp     dm-corrosion.tmp      dm-zion.tmp
aoa-corrosion.tmp    dm-crucible2k8.tmp   dm-zorn.tmp
aoa-frost2k9.tmp     dm-deimos2k9.tmp      Fafa.cfg
aoa-frost.tmp         dm-dismal2k8.tmp      Gamara.cfg
aoa-morpheus.tmp     dm-dread.tmp      Ghidora.cfg
aoa-zorn.tmp         dm-dynamo2k8.tmp      Hedorah.cfg
Astral.cfg         dm-eternal.tmp      Johnny.cfg
Beavis.cfg         dm-europa2k8.tmp      Martian_is_lame.cfg
Butthead.cfg         dm-furious2k8.tmp      Martian_jr.cfg
Cyborg.cfg         dm-horus.tmp      Martian_owns_u.cfg
db-chromium.tmp      dm-invasion.tmp      Mogera.cfg
db-icarus.tmp         dm-leviathan2k8.tmp  Mothra.cfg
db-vesuvius.tmp      dm-liberation.tmp      nav
Destoroyah.cfg         dm-omega2k8.tmp      Real_Martian.cfg
dm-aquous.tmp         dm-saucer2k9.tmp      sample.cfg
dm-atlantis2k8.tmp   dm-saucer.tmp      Squirtney.cfg
dm-babel.tmp         dm-titan2k8.tmp      Stryker.cfg
dm-beyond.tmp         dm-turbo2k8.tmp      team.tmp
dm-bloodfactory.tmp  dm-vesuvius.tmp      Yoz.cfg
dm-chasmatic2k9.tmp  dm-violator.tmp

./trunk/botinfo/nav:
aoa-atlantis.nod    dm-aquous.nod     dm-invasion.nod
aoa-corrosion.nod   dm-atlantis2k8.nod     dm-leviathan2k8.nod
aoa-frost2k9.nod    dm-babel.nod     dm-leviathan.nod
aoa-frost.nod        dm-beyond.nod     dm-liberation.nod
aoa-morpheus.nod    dm-bloodfactory.nod  dm-obsidian2.nod
aoa-zorn.nod        dm-blood.nod     dm-omega2k8.nod
cp-grindery.nod     dm-chasmatic2k9.nod  dm-omega.nod
cp-ribeye.nod        dm-chasmatic.nod     dm-saucer.nod
ctf-atlantis.nod    dm-command2k9.nod     dm-titan2k8.nod
ctf-chromium.nod    dm-corrosion.nod     dm-titan.nod
ctf-corrosion.nod   dm-crucible2k8.nod     dm-turbo2k8.nod
ctf-cryogenic.nod   dm-deimos2k9.nod     dm-vesuvius.nod
ctf-europa2k8.nod   dm-deimos.nod     dm-violator.nod
ctf-frost2k9.nod    dm-dismal2k8.nod     dm-warmachine2k9.nod
ctf-frost.nod        dm-dismal.nod     dm-warmachine.nod
ctf-icarus2.nod     dm-dread.nod     dm-zion.nod
ctf-stronghold.nod  dm-dynamo2k8.nod     dm-zorn.nod
ctf-terminal.nod    dm-dynamo2.nod     tca-corrosion.nod
ctf-titan2k8.nod    dm-eternal.nod     tca-cryogenic.nod
ctf-vesuvius.nod    dm-europa2k8.nod     tca-europa2k8.nod
ctf-zorn.nod        dm-frontier2.nod     tca-frost.nod
db-chromium.nod     dm-furious2k8.nod     tca-titan2k8.nod
db-icarus.nod        dm-grindery.nod     tca-zion.nod
db-vesuvius.nod     dm-horus.nod

./trunk/data1:
default.cfg  game.so      levelshots  models     players  textures
env         gamex86.dll  maps          particles  scripts  vehicles
fonts         gfx      maps.lst    pics     sound

./trunk/data1/env:
alienbk.tga  egyptrt.tga  hellft.tga     seabk.tga     space1rt.tga
aliendn.tga  egyptup.tga  helllf.tga     seadn.tga     space1up.tga
alienft.tga  greenbk.tga  hellrt.tga     seaft.tga     tekcitybk.tga
alienlf.tga  greendn.tga  hellup.tga     sealf.tga     tekcitydn.tga
alienrt.tga  greenft.tga  martianbk.tga  seart.tga     tekcityft.tga
alienup.tga  greenlf.tga  martiandn.tga  seaup.tga     tekcitylf.tga
egyptbk.tga  greenrt.tga  martianft.tga  space1bk.tga  tekcityrt.tga
egyptdn.tga  greenup.tga  martianlf.tga  space1dn.tga  tekcityup.tga
egyptft.tga  hellbk.tga   martianrt.tga  space1ft.tga
egyptlf.tga  helldn.tga   martianup.tga  space1lf.tga

./trunk/data1/fonts:
default.tga  digital.tga  fat.tga

./trunk/data1/gfx:
aaglow.tga         electrics2.tga         noise.tga
adrenalbase.tga         electrics3a.tga     plate5fx.tga
adrenalmask.tga         electrics3b.tga     purpleline.tga
alienarena2gl.tga     electrics3d.tga     quadbase.tga
bannerfx.tga         electrics3.tga         quadmask.tga
bconsole2.tga         electrics.tga         radar
bconsole.tga         flares             rain.tga
beam1.tga         flash_noise.jpg     rayfx.tga
beam2.tga         flash.tga         redcircuit.tga
beamfx.tga         gamarafx.tga         redlightning.tga
blasterfx.tga         glightning.tga         reflect.tga
bluelightning2.tga     gold.tga         rlauncherfx.tga
bluelightning.tga     grapplefx.tga         r_lightning.tga
bubbles.tga         grass.tga         sconsole.tga
caustics.tga         grchrome.tga         shard_fx.tga
chrome2.tga         greencircuit2.tga     shardmask.tga
chrome.tga         greencircuit.tga     skullglow.tga
citymask.tga         greenlightning.tga     smartgunmask.tga
cloudsspace.tga         greenline.tga         sun1.jpg
clouds.tga         hastebase.tga         sun2.jpg
cloudsthick.tga         hastemask.tga         sun.jpg
comp1.tga         hconsole2.tga         tekwallmask.tga
comp2.tga         hconsole3.tga         trim2mask.tga
cpribeyereflection.tga     hconsole.tga         vaporbase.tga
disruptormask.tga     hoverfx.tga         vapormask.tga
distortwave.jpg         leaves1.tga         violatorfx.tga
dmaquousreflection.tga     lightning.tga         water
dmbeyondreflection.tga     m_banner_main_mask.tga  w_distortwave.jpg
dmdreadreflection.tga     menubar1.tga         w_flash_noise.jpg
dmturboreflection.tga     menubar2.tga         wt_distortwave.jpg
e6launchengine_glow.tga  metal3glow.tga         wt_flash_noise.jpg
egypt5_mask.tga         mirrorspec.tga         yellowline.tga

./trunk/data1/gfx/flares:
flare0.tga

./trunk/data1/gfx/radar:
around.tga  radarmap.tga

./trunk/data1/gfx/water:
distort1.tga  normal1.tga

./trunk/data1/levelshots:
aoa-atlantis.jpg   db-icarus.jpg    dm-invasion.jpg
aoa-atlantis.txt   db-icarus.txt    dm-invasion.txt
aoa-corrosion.jpg  db-vesuvius.jpg    dm-leviathan2k8.jpg
aoa-corrosion.txt  db-vesuvius.txt    dm-leviathan2k8.txt
aoa-frost2k9.jpg   dm-aquous.jpg    dm-liberation.jpg
aoa-frost2k9.txt   dm-aquous.txt    dm-liberation.txt
aoa-frost.jpg       dm-atlantis2k8.jpg    dm-omega2k8.jpg
aoa-frost.txt       dm-atlantis2k8.txt    dm-omega2k8.txt
aoa-morpheus.jpg   dm-babel.jpg        dm-omega.jpg
aoa-morpheus.txt   dm-babel.txt        dm-saucer2k9.jpg
aoa-zorn.jpg       dm-beyond.jpg    dm-saucer2k9.txt
aoa-zorn.txt       dm-beyond.txt    dm-saucer.jpg
cft-corrosion.txt  dm-bloodfactory.jpg    dm-saucer.txt
cp-grindery.jpg    dm-bloodfactory.txt    dm-titan2k8.jpg
cp-grindery.txt    dm-chasmatic2k9.jpg    dm-titan2k8.txt
cp-ribeye.jpg       dm-chasmatic2k9.txt    dm-turbo2k8.jpg
cp-ribeye.txt       dm-command2k9.jpg    dm-turbo2k8.txt
ctf-atlantis.jpg   dm-command2k9.txt    dm-vesuvius.jpg
ctf-atlantis.txt   dm-corrosion.jpg    dm-vesuvius.txt
ctf-chromium.jpg   dm-corrosion.txt    dm-violator.jpg
ctf-chromium.txt   dm-crucible2k8.jpg    dm-violator.txt
ctf-corrosion.jpg  dm-crucible2k8.txt    dm-warmachine2k9.jpg
ctf-cryogenic.jpg  dm-crucible.jpg    dm-warmachine2k9.txt
ctf-cryogenic.txt  dm-crucible.txt    dm-warmachine.txt
ctf-europa2k8.jpg  dm-deimos2k9.jpg    dm-zion.jpg
ctf-europa2k8.txt  dm-deimos2k9.txt    dm-zion.txt
ctf-frost2k9.jpg   dm-dismal2k8.jpg    dm-zorn.jpg
ctf-frost2k9.txt   dm-dismal2k8.txt    dm-zorn.txt
ctf-frost.jpg       dm-dread.jpg        tca-corrosion.jpg
ctf-frost.txt       dm-dread.txt        tca-corrosion.txt
ctf-icarus2.jpg    dm-dynamo2k8.jpg    tca-cryogenic.jpg
ctf-icarus2.txt    dm-dynamo2k8.txt    tca-cryogenic.txt
ctf-titan2k8.jpg   dm-eternal.jpg    tca-europa2k8.jpg
ctf-titan2k8.txt   dm-eternal.txt    tca-europa2k8.txt
ctf-vesuvius.jpg   dm-europa2k8.jpg    tca-frost.jpg
ctf-vesuvius.txt   dm-europa2k8.txt    tca-frost.txt
ctf-zorn.jpg       dm-furious2k8.jpg    tca-titan2k8.jpg
ctf-zorn.txt       dm-furious2k8.txt    tca-titan2k8.txt
db-chromium.jpg    dm-horus.jpg        tca-zion.jpg
db-chromium.txt    dm-horus.txt        tca-zion.txt

./trunk/data1/maps:
aoa-atlantis.bsp    db-vesuvius.bsp     dm-saucer2k9.bsp
aoa-corrosion.bsp   dm-aquous.bsp     dm-saucer.bsp
aoa-frost2k9.bsp    dm-atlantis2k8.bsp     dm-titan2k8.bsp
aoa-morpheus.bsp    dm-babel.bsp     dm-turbo2k8.bsp
aoa-zorn.bsp        dm-beyond.bsp     dm-vesuvius.bsp
compile.bat        dm-bloodfactory.bsp  dm-violator.bsp
cp-grindery.bsp     dm-chasmatic2k9.bsp  dm-warmachine2k9.bsp
cp-ribeye.bsp        dm-command2k9.bsp     dm-zion.bsp
ctf-atlantis.bsp    dm-corrosion.bsp     dm-zorn.bsp
ctf-chromium.bsp    dm-crucible2k8.bsp     lighttest.bsp
ctf-corrosion.bsp   dm-deimos2k9.bsp     mapsrc
ctf-cryogenic.bsp   dm-dismal2k8.bsp     meshes
ctf-europa2k8.bsp   dm-dread.bsp     scripts
ctf-frost2k9.bsp    dm-dynamo2k8.bsp     tca-corrosion.bsp
ctf-icarus2.bsp     dm-eternal.bsp     tca-cryogenic.bsp
ctf-stronghold.bsp  dm-europa2k8.bsp     tca-europa2k8.bsp
ctf-terminal.bsp    dm-furious2k8.bsp     tca-europa.bsp
ctf-titan2k8.bsp    dm-horus.bsp     tca-frost.bsp
ctf-vesuvius.bsp    dm-invasion.bsp     tca-titan2k8.bsp
ctf-zorn.bsp        dm-leviathan2k8.bsp  tca-zion.bsp
db-chromium.bsp     dm-liberation.bsp
db-icarus.bsp        dm-omega2k8.bsp

./trunk/data1/maps/mapsrc:
aoa-atlantis.map    dm-beyond.map     dm-leviathan.map
aoa-corrosion.map   dm-bloodfactory.map  dm-liberation.map
aoa-frost2k9.map    dm-bootcamp.map     dm-omega2k8.map
aoa-morpheus.map    dm-chasmatic2k9.map  dm-omega.map
aoa-zorn.map        dm-chasmatic.map     dm-saucer2k9.map
cp-grindery.map     dm-command2k9.map     dm-saucer.map
cp-ribeye.map        dm-command.map     dm-titan2k8.map
ctf-atlantis.map    dm-corrosion.map     dm-titan.map
ctf-chromium.map    dm-crucible.map     dm-turbo2k8.map
ctf-corrosion.map   dm-deimos2k9.map     dm-turbo.map
ctf-cryogenic.map   dm-deimos.map     dm-vesuvius.map
ctf-europa2k8.map   dm-dismal2k8.map     dm-violator.map
ctf-europa.map        dm-dismal.map     dm-warmachine2k9.map
ctf-frost2k9.map    dm-dread.map     dm-warmachine.map
ctf-icarus.map        dm-dynamo2k8.map     dm-zion.map
ctf-titan2k8.map    dm-dynamo2.map     dm-zorn.map
ctf-titan.map        dm-eternal.map     tca-corrosion.map
ctf-vesuvius.map    dm-europa2k8.map     tca-cryogenic.map
ctf-zorn.map        dm-europa.map     tca-europa2k8.map
db-chromium.map     dm-frontier2.map     tca-europa.map
db-icarus.map        dm-furious2k8.map     tca-frost.map
db-vesuvius.map     dm-furious.map     tca-titan2k8.map
dm-aquous.map        dm-grindery.map     tca-titan.map
dm-atlantis2k8.map  dm-horus.map     tca-zion.map
dm-atlantis.map     dm-invasion.map
dm-babel.map        dm-leviathan2k8.map

./trunk/data1/maps/meshes:
arch_fx.tga           dualpipes_normal.jpg  piston_normal.jpg
arch.md2           electrodecover.md2    piston.tga
arch_normal.jpg        electrode.md2         pulsar.md2
arch.tga           electrode.tga         pulsar_normal.jpg
barrel.jpg           flagpad.md2         pulsar.tga
barrel.md2           flagpad_normal.tga    railcarglass.md2
bentconduit.md2        flagpad.tga         railcar.jpg
bignode_fx.tga           generator.jpg         railcarmartian.md2
bignode.jpg           generator.md2         railcar.md2
bignode.md2           generator_normal.jpg  railcarmhelmet.md2
bignode_normal.jpg     hanger.md2         railcar_normal.jpg
bigribpipe.jpg           hanger_normal.jpg     ribtube1.md2
bigribpipe.md2           hanger.tga         ribtube2.md2
bigribpipe_normal.jpg  hangingmartian.md2    ribtube.jpg
brainjarcover.md2      hangingmhelmet.md2    ribtube_normal.jpg
brainjar.md2           hatch.jpg         sconduit1.md2
brainjar_normal.tga    hatch.md2         sconduit2.md2
brainjar.tga           hatch_normal.jpg      scopecover.md2
cables2.md2           injector.jpg         scope.md2
cables3.md2           injector.md2         scope_normal.tga
cables.jpg           injector_normal.jpg   scope.tga
cables.md2           lamp2_fx.tga         spingear_fx.tga
cannister.jpg           lamp2.jpg         spingear.jpg
cannister.md2           lamp2.md2         spingear.md2
cannister_normal.jpg   lamp2_normal.jpg      spingear_normal.jpg
clamps.jpg           martian.jpg         spintube.jpg
clamps.md2           martian.md2         spintube.md2
clamps_normal.jpg      metpipe1.md2         spintube_normal.jpg
cmdconsole_fx.tga      metpipe2.md2         straightconduit.md2
cmdconsole.jpg           metpipe3.md2         toxicbarrell.jpg
cmdconsole.md2           mhelmet.md2         toxicbarrell.md2
cmdconsole_normal.jpg  monitor2.md2         tubecover.md2
conduit.jpg           monitor.jpg         tube.md2
conduit_normal.jpg     monitormask.tga         tube.tga
controls_fx.tga        monitor.md2         unit.jpg
controls.md2           mpa1.jpg             unit.md2
controls_normal.tga    mpa2.jpg             unit_normal.jpg
controls.tga           pipes1.jpg         weaponpad.md2
dome.md2           pipes1_normal.jpg     weaponpad_normal.tga
dualpipes.jpg           pipes.md2         weaponpad.tga
dualpipes.md2           piston.md2

./trunk/data1/maps/scripts:
aoa2.fog        db-vesuvius.fog     dm-invasion.mus
aoa-atlantis.mus    db-vesuvius.mus     dm-leviathan2k8.fog
aoa-corrosion.fog   dm-aquous.fog     dm-leviathan2k8.mus
aoa-corrosion.mus   dm-aquous.mus     dm-liberation.fog
aoa-frost2k9.fog    dm-atlantis2k8.mus     dm-liberation.mus
aoa-frost2k9.mus    dm-babel.fog     dm-omega2k8.mus
aoa-frost.fog        dm-babel.mus     dm-saucer2k9.fog
aoa-frost.mus        dm-beyond.mus     dm-saucer2k9.mus
aoa-morpheus.mus    dm-bloodfactory.fog  dm-saucer.fog
aoa-zorn.mus        dm-bloodfactory.mus  dm-saucer.mus
cp-grindery.mus     dm-chasmatic2k9.fog  dm-titan2k8.mus
cp-ribeye.mus        dm-chasmatic2k9.mus  dm-turbo2k8.fog
ctf-atlantis.mus    dm-chasmatic.mus     dm-turbo2k8.mus
ctf-chromium.mus    dm-command2k9.fog     dm-vesuvius.fog
ctf-corrosion.fog   dm-command2k9.mus     dm-vesuvius.mus
ctf-corrosion.mus   dm-corrosion.fog     dm-violator.mus
ctf-cryogenic.fog   dm-corrosion.mus     dm-warmachine2k9.fog
ctf-cryogenic.mus   dm-crucible2k8.fog     dm-warmachine2k9.mus
ctf-europa2k8.mus   dm-crucible2k8.mus     dm-warmachine.mus
ctf-frost2k9.fog    dm-deimos2k9.mus     dm-zion.mus
ctf-frost2k9.mus    dm-dismal2k8.fog     dm-zorn.mus
ctf-frost.fog        dm-dismal2k8.mus     tca-corrosion.fog
ctf-icarus2.mus     dm-dread.mus     tca-corrosion.mus
ctf-stronghold.mus  dm-dynamo2k8.fog     tca-cryogenic.fog
ctf-terminal.mus    dm-dynamo2k8.mus     tca-cryogenic.mus
ctf-titan2k8.mus    dm-eternal.fog     tca-europa2k8.mus
ctf-vesuvius.fog    dm-eternal.mus     tca-frost.fog
ctf-vesuvius.mus    dm-europa2k8.mus     tca-frost.mus
ctf-zorn.mus        dm-furious2k8.fog     tca-titan2k8.mus
db-chromium.mus     dm-furious2k8.mus     tca-zion.mus
db-icarus.mus        dm-horus.mus     tourney0.fog

./trunk/data1/models:
cow  items  misc  objects  weapons

./trunk/data1/models/cow:
helmet.md2  skin.tga  tris.md2

./trunk/data1/models/items:
adrenaline  ammo  armor  flags    haste  healing    invulner  quaddama  sproing

./trunk/data1/models/items/adrenaline:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/ammo:
bullets  cells    grenades  rockets  shells  skin_normal.tga

./trunk/data1/models/items/ammo/bullets:
medium

./trunk/data1/models/items/ammo/bullets/medium:
skin.tga  tris.md2

./trunk/data1/models/items/ammo/cells:
medium

./trunk/data1/models/items/ammo/cells/medium:
cell.tga  tris.md2

./trunk/data1/models/items/ammo/grenades:
medium

./trunk/data1/models/items/ammo/grenades/medium:
skin.tga  tris.md2

./trunk/data1/models/items/ammo/rockets:
medium

./trunk/data1/models/items/ammo/rockets/medium:
skin.tga  tris.md2

./trunk/data1/models/items/ammo/shells:
medium

./trunk/data1/models/items/ammo/shells/medium:
skin.tga  tris.md2

./trunk/data1/models/items/armor:
body  combat  jacket  shard  skin_normal.tga

./trunk/data1/models/items/armor/body:
skin.tga  tris.md2

./trunk/data1/models/items/armor/combat:
skin.tga  tris.md2

./trunk/data1/models/items/armor/jacket:
skin.tga  tris.md2

./trunk/data1/models/items/armor/shard:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/flags:
blue.tga  flag1.md2  flag2.md2    red.tga

./trunk/data1/models/items/haste:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/healing:
globe  large  medium  small

./trunk/data1/models/items/healing/globe:
skin.tga  tris.md2

./trunk/data1/models/items/healing/large:
skin.tga  tris.md2

./trunk/data1/models/items/healing/medium:
skin.tga  tris.md2

./trunk/data1/models/items/healing/small:
skin.tga  tris.md2

./trunk/data1/models/items/invulner:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/items/quaddama:
skin_normal.tga  skin.tga  tris.md2  unit.md2

./trunk/data1/models/items/sproing:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/misc:
electrode  lamp  lamp2    pod  receptor  scope  spiderpod  tube

./trunk/data1/models/misc/electrode:
cover.md2  electrode.tga  tris.md2

./trunk/data1/models/misc/lamp:
lamp.tga  tris.md2

./trunk/data1/models/misc/lamp2:
lamp2.tga  tris.md2

./trunk/data1/models/misc/pod:
pod.tga  tris.md2

./trunk/data1/models/misc/receptor:
bulb.md2  receptor.tga    tris.md2

./trunk/data1/models/misc/scope:
cover.md2  scope.tga  tris.md2

./trunk/data1/models/misc/spiderpod:
skin.tga  tris.md2

./trunk/data1/models/misc/tube:
cover.md2  tris.md2  tube.tga

./trunk/data1/models/objects:
blank  debris1    debris3  electroball  gibs   rocket
brass  debris2    dmspot     fireball     laser

./trunk/data1/models/objects/blank:
skin.tga  tris.md2

./trunk/data1/models/objects/brass:
skin.jpg  tris.md2

./trunk/data1/models/objects/debris1:
skin.tga  tris.md2

./trunk/data1/models/objects/debris2:
skin.tga  tris.md2

./trunk/data1/models/objects/debris3:
skin.tga  tris.md2

./trunk/data1/models/objects/dmspot:
skin_normal.tga  skin.tga  tris.md2

./trunk/data1/models/objects/electroball:
skin.tga  tris.md2

./trunk/data1/models/objects/fireball:
skin.tga  tris.md2

./trunk/data1/models/objects/gibs:
mart_gut  skin_normal.jpg  sm_meat

./trunk/data1/models/objects/gibs/mart_gut:
skin.jpg  tris.md2

./trunk/data1/models/objects/gibs/sm_meat:
skin.jpg  tris.md2

./trunk/data1/models/objects/laser:
skin.tga  tris.md2

./trunk/data1/models/objects/rocket:
skin.tga  tris.md2

./trunk/data1/models/weapons:
g_bfg      g_launch  g_rocket  v_bfg    v_hyperb  v_rocket  v_violator
g_chain   g_machn   g_shotg   v_blast  v_machn     v_shotg
g_hyperb  g_rail    g_shotg2  v_chain  v_rail     v_shotg2

./trunk/data1/models/weapons/g_bfg:
tris.md2

./trunk/data1/models/weapons/g_chain:
tris.md2

./trunk/data1/models/weapons/g_hyperb:
cover.md2  tris.md2

./trunk/data1/models/weapons/g_launch:
skin.tga  tris.md2

./trunk/data1/models/weapons/g_machn:
tris.md2

./trunk/data1/models/weapons/g_rail:
tris.md2

./trunk/data1/models/weapons/g_rocket:
cover.md2  tris.md2

./trunk/data1/models/weapons/g_shotg:
tris.md2

./trunk/data1/models/weapons/g_shotg2:
tris.md2

./trunk/data1/models/weapons/v_bfg:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_blast:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_chain:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_hyperb:
cover.md2  skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_machn:
tris.md2

./trunk/data1/models/weapons/v_rail:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_rocket:
cover.md2  skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_shotg:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_shotg2:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/models/weapons/v_violator:
skin.jpg  skin_normal.tga  tris.md2

./trunk/data1/particles:
aflash.tga     deathfield2.tga  reflect.tga      ripples.tga
basic.tga     deathfield.tga   r_explod_1.tga  sayicon.tga
beam.tga     dflash.tga      r_explod_2.tga  shell.tga
bflash.tga     explosion.tga      r_explod_3.tga  smoke_org.tga
blood.tga     flag.tga      r_explod_4.tga  smoke.tga
bubble.tga     flare.tga      r_explod_5.tga  voltage.tga
bullethole2.tga  leaderfield.tga  r_explod_6.tga  watersplash.tga
bullethole.tga     logo.tga      r_explod_7.tga
cflash.tga     puff.tga      ring.tga

./trunk/data1/pics:
a_bullets.tga        i_health.tga        num_5.tga
a_cells.tga        inventory.tga        num_6.tga
a_grenades.tga        i_score.tga            num_7.tga
anum_0.tga        i_team1.tga            num_8.tga
anum_1.tga        i_team2.tga            num_9.tga
anum_2.tga        m_bots.tga            num_minus.tga
anum_3.tga        m_controls.tga        options.tga
anum_4.tga        m_cursor0.tga        p_adrenaline.tga
anum_5.tga        m_dmoptions.tga        p_haste.tga
anum_6.tga        menu_back.jpg        p_invis.tga
anum_7.tga        m_joinserver.tga        p_invulnerability.tga
anum_8.tga        m_main_game_sel.tga     playerbox.tga
anum_9.tga        m_main_game.tga        p_powered.tga
anum_minus.tga        m_main_host_sel.tga     p_quad.tga
a_rockets.tga        m_main_host.tga        p_rewardpts.tga
a_shells.tga        m_main_join_sel.tga     p_sproing.tga
a_slugs.tga        m_main_join.tga        redplayerbox.tga
backtile.pcx        m_main_mont0.tga        rocketlauncher.tga
bar_background.tga  m_main_mont1.tga        sbfctf1.tga
bar_loading.tga     m_main_mont2.tga        sbfctf2.tga
beamgun.tga        m_main_mont3.tga        smartgun.tga
blaster.tga        m_main_mont4.tga        statbox.tga
blueplayerbox.tga   m_main_mont5.tga        strafer.tga
bomber.tga        m_main_options_sel.tga  tag1.tga
bots            m_main_options.tga        tag2.tga
ch1.tga            m_main_quit_sel.tga     team1.tga
ch2.tga            m_main_quit.tga        team2.tga
ch3.tga            m_main.tga            timer.tga
chaingun.tga        m_main_video_sel.tga    uparrow.tga
colormap.pcx        m_main_video.tga        vaporizor.tga
conback.tga        m_mouse_cursor.tga        violator.tga
conchars.tga        m_mutators.tga        w_bfg.tga
crosshairs        m_options.tga        w_blaster.tga
ctf1.tga        m_player.tga        w_chaingun.tga
ctf2.tga        m_quit.tga            w_glauncher.tga
disruptor.tga        m_single.tga        w_hyperblaster.tga
dnarrow.tga        m_startserver.tga        w_machinegun.tga
flamethrower.tga    m_video.tga            w_railgun.tga
grapple.tga        net.tga            w_rlauncher.tga
help.tga        num_0.tga            w_shotgun.tga
hover.tga        num_1.tga            w_sshotgun.tga
huds            num_2.tga            zoomscope1.tga
i_flag1.tga        num_3.tga            zoomscope2.tga
i_flag2.tga        num_4.tga            zoomscope3.tga

./trunk/data1/pics/bots:
enforcer  martiancyborg  martianenforcer

./trunk/data1/pics/bots/enforcer:
blue_i.jpg  default_i.jpg  red_i.jpg  stryker_i.jpg

./trunk/data1/pics/bots/martiancyborg:
blue_i.jpg  default_i.jpg  red_i.jpg

./trunk/data1/pics/bots/martianenforcer:
blue_i.jpg  default_i.jpg  gamara_i.jpg  red_i.jpg

./trunk/data1/pics/crosshairs:
alien2a.tga    hardcorech.tga     mechano.tga     robot.tga
alien2b.tga    havoc2.tga     ncool.tga     sniper.tga
alien2.tga     havoc3.tga     nile2.tga     sungod.tga
alien.tga      havoc.tga     nile3.tga     tech2.tga
chexcross.tga  intimidator2.tga  nile.tga     tech.tga
dot1.tga       intimidator3.tga  rage_cross.tga  transcircle.tga
freezy.tga     intimidator.tga     rgb.tga     vista.tga

./trunk/data1/pics/huds:
20061.tga     classic2.tga      gtv1.tga      retro2.tga
20062.tga     cleanblue1.tga   gtv2.tga      talon1.tga
20071.tga     cleanblue2.tga   marscreen1.tga  talon2.tga
20072.tga     cleangreen1.tga  marscreen2.tga  terminal-blue1.tga
8bit1.tga     cleangreen2.tga  mechanic1.tga   terminal-blue2.tga
8bit2.tga     cleanred1.tga      mechanic2.tga   terminal-green1.tga
alien1.tga     cleanred2.tga      nki_dark1.tga   terminal-green2.tga
alien2.tga     corpse1.tga      nki_dark2.tga   terminal-purple1.tga
alienblood1.tga  corpse2.tga      nki_darkb1.tga  terminal-purple2.tga
alienblood2.tga  cpu1.tga      nki_darkb2.tga  terminal-red1.tga
blood1.tga     cpu2.tga      oldskool1.tga   terminal-red2.tga
blood2.tga     freezy1.tga      oldskool2.tga   therock1.tga
classic1.tga     freezy2.tga      retro1.tga      therock2.tga

./trunk/data1/players:
commander  enforcer  lauren  martiancyborg  martianenforcer  slashbot

./trunk/data1/players/commander:
blue_i.jpg        drown1.wav       pain25_2.wav   w_chaingun.md2
blue.jpg        fall1.wav       pain50_1.wav   weapon.jpg
bump1.wav        fall2.wav       pain50_2.wav   weapon.md2
death1.wav        gurp1.wav       pain75_1.wav   w_hyperblaster.md2
death2.wav        gurp2.wav       pain75_2.wav   w_machinegun.md2
death3.wav        human       red_i.jpg      w_railgun.md2
death4.wav        jump1.wav       red.jpg      w_rlauncher.md2
default_i.jpg        pain100_1.wav  tris.md2      w_shotgun.md2
default.jpg        pain100_2.wav  w_bfg.md2      w_sshotgun.md2
default_normal.jpg  pain25_1.wav   w_blaster.md2  w_violator.md2

./trunk/data1/players/enforcer:
arm.md2            fall1.wav       pain25_1.wav   w_blaster.md2
blue_i.jpg        fall2.wav       pain25_2.wav   w_chaingun.md2
blue.jpg        gurp1.wav       pain50_1.wav   weapon.jpg
body.md2        gurp2.wav       pain50_2.wav   weapon.md2
bump1.wav        head.md2       pain75_1.wav   w_hyperblaster.md2
death1.wav        helmet.md2       pain75_2.wav   w_machinegun.md2
death2.wav        human       red_i.jpg      w_railgun.md2
death3.wav        jump1.wav       red.jpg      w_rlauncher.md2
death4.wav        leg.md2       stryker_i.jpg  w_shotgun.md2
default_i.jpg        lod1.md2       stryker.jpg      w_sshotgun.md2
default.jpg        lod2.md2       tris.md2      w_violator.md2
default_normal.tga  pain100_1.wav  usegibs
drown1.wav        pain100_2.wav  w_bfg.md2

./trunk/data1/players/lauren:
arm.md2            drown1.wav       pain25_2.wav    weapon.jpg
blue_i.jpg        fall1.wav       pain50_1.wav    weapon.md2
blue.jpg        fall2.wav       pain50_2.wav    w_hyperblaster.md2
body.md2        gurp1.wav       pain75_1.wav    w_machinegun.md2
bump1.wav        gurp2.wav       pain75_2.wav    w_railgun.md2
death1.wav        head.md2       red_i.jpg       w_rlauncher.md2
death2.wav        human       red.jpg       w_shotgun.md2
death3.wav        jump1.wav       tris.md2       w_sshotgun.md2
death4.wav        leg.md2       usegibs       w_violator.md2
default_i.jpg        pain100_1.wav  w_bfg.md2
default.jpg        pain100_2.wav  w_blaster.md2
default_normal.tga  pain25_1.wav   w_chaingun.md2

./trunk/data1/players/martiancyborg:
blue_i.jpg        fall1.wav       pain25_2.wav   w_chaingun.md2
blue.jpg        fall2.wav       pain50_1.wav   weapon.md2
bump1.wav        gurp1.wav       pain50_2.wav   weapon.tga
death1.wav        gurp2.wav       pain75_1.wav   w_hyperblaster.md2
death2.wav        helmet.md2       pain75_2.wav   w_machinegun.md2
death3.wav        jump1.wav       red_i.jpg      w_railgun.md2
death4.wav        lod1.md2       red.jpg      w_rlauncher.md2
default_i.jpg        lod2.md2       robot      w_shotgun.md2
default.jpg        pain100_1.wav  tris.md2      w_sshotgun.md2
default_normal.tga  pain100_2.wav  w_bfg.md2      w_violator.md2
drown1.wav        pain25_1.wav   w_blaster.md2

./trunk/data1/players/martianenforcer:
alien            drown1.wav      lod1.md2     usegibs
arm.md2            fall1.wav      lod2.md2     w_bfg.md2
blue_i.jpg        fall2.wav      pain100_1.wav  w_blaster.md2
blue.jpg        gamara_i.jpg  pain100_2.wav  w_chaingun.md2
body.md2        gamara.jpg      pain25_1.wav     weapon.md2
bump1.wav        gasp1.wav      pain25_2.wav     weapon.tga
death1.wav        gasp2.wav      pain50_1.wav     w_hyperblaster.md2
death2.wav        gurp1.wav      pain50_2.wav     w_machinegun.md2
death3.wav        gurp2.wav      pain75_1.wav     w_railgun.md2
death4.wav        head.md2      pain75_2.wav     w_rlauncher.md2
default_i.jpg        helmet.md2      red_i.jpg     w_shotgun.md2
default.jpg        jump1.wav      red.jpg     w_sshotgun.md2
default_normal.tga  leg.md2      tris.md2     w_violator.md2

./trunk/data1/players/slashbot:
blue_i.jpg        drown1.wav       pain50_1.wav   w_chaingun.md2
blue.jpg        fall1.wav       pain50_2.wav   weapon.jpg
bump1.wav        fall2.wav       pain75_1.wav   weapon.md2
death1.wav        gurp1.wav       pain75_2.wav   w_hyperblaster.md2
death2.wav        gurp2.wav       red_i.jpg      w_machinegun.md2
death3.wav        jump1.wav       red.jpg      w_railgun.md2
death4.wav        pain100_1.wav  robot      w_rlauncher.md2
default_i.jpg        pain100_2.wav  tris.md2      w_shotgun.md2
default.jpg        pain25_1.wav   w_bfg.md2      w_sshotgun.md2
default_normal.jpg  pain25_2.wav   w_blaster.md2  w_violator.md2

./trunk/data1/scripts:
caustics.rscript     fragment_shader.glsl        players.rscript
chrome.rscript         gunmen.rscript            textures.rscript
consoles.rscript     maps                vertex_shader.glsl
electrics2.rscript     menu.rscript            water1.arbf
electrics3.rscript     mesh_fragment_shader.glsl  water_fragment_shader.glsl
electrics.rscript     mesh_vertex_shader.glsl    water.rscript
fb_fragment_shader.glsl  models.rscript            water_vertex_shader.glsl
fb_vertex_shader.glsl     normals

./trunk/data1/scripts/maps:
aoa-atlantis.rscript    dm-aquous.rscript     dm-leviathan2k8.rscript
aoa-corrosion.rscript    dm-atlantis2k8.rscript     dm-leviathan.rscript
aoa-frost2k9.rscript    dm-babel.rscript     dm-liberation.rscript
aoa-morpheus.rscript    dm-beyond.rscript     dm-omega2k8.rscript
aoa-zorn.rscript    dm-bloodfactory.rscript  dm-saucer2k9.rscript
cp-grindery.rscript    dm-chasmatic2k9.rscript  dm-saucer.rscript
cp-ribeye.rscript    dm-chasmatic.rscript     dm-titan2k8.rscript
ctf-atlantis.rscript    dm-command2k9.rscript     dm-turbo2k8.rscript
ctf-chromium.rscript    dm-corrosion.rscript     dm-vesuvius.rscript
ctf-corrosion.rscript    dm-crucible2k8.rscript     dm-violator.rscript
ctf-cryogenic.rscript    dm-crucible.rscript     dm-warmachine2k9.rscript
ctf-europa2k8.rscript    dm-deimos2k9.rscript     dm-warmachine.rscript
ctf-frost2k9.rscript    dm-dismal2k8.rscript     dm-zion.rscript
ctf-icarus2.rscript    dm-dread.rscript     dm-zorn.rscript
ctf-stronghold.rscript    dm-dynamo2k8.rscript     tca-corrosion.rscript
ctf-terminal.rscript    dm-dynamo2.rscript     tca-cryogenic.rscript
ctf-titan2k8.rscript    dm-eternal.rscript     tca-europa2k8.rscript
ctf-vesuvius.rscript    dm-europa2k8.rscript     tca-frost.rscript
ctf-zorn.rscript    dm-furious2k8.rscript     tca-titan2k8.rscript
db-chromium.rscript    dm-grindery.rscript     tca-zion.rscript
db-icarus.rscript    dm-horus.rscript
db-vesuvius.rscript    dm-invasion.rscript

./trunk/data1/scripts/normals:
normals.rscript

./trunk/data1/sound:
doors  items  misc  music  player  smallmech  taunts  vehicles    weapons  world

./trunk/data1/sound/doors:
dr1_end.wav  dr1_mid.wav  dr1_strt.wav

./trunk/data1/sound/items:
damage2.wav   haste.wav     powerup.wav   protect.wav      sproing.wav
damage3.wav   l_health.wav  protect2.wav  respawn1.wav
damage.wav    m_health.wav  protect3.wav  s_health.wav
hasteout.wav  n_health.wav  protect4.wav  sproingout.wav

./trunk/data1/sound/misc:
1frags.wav        blue_scores.wav    menu2.wav       red_wins.wav
2frags.wav        bluevulnerable.wav    menu3.wav       reject.wav
3frags.wav        blue_wins_ctf.wav    one.wav           spawn1.wav
am_pkup.wav        blue_wins.wav    pc_up.wav       talk1.wav
ar1_pkup.wav        cow            rampage.wav       talk.wav
ar2_pkup.wav        db_pickup.wav    red_picked.wav       tele1.wav
ar3_pkup.wav        db_score.wav    redpndisabled.wav  tele_up.wav
bigtele.wav        fight.wav        redpnenabled.wav   three.wav
blue_picked.wav     godlike.wav        red_returned.wav   trigger1.wav
bluepndisabled.wav  hit.wav        red_scores.wav       two.wav
bluepnenabled.wav   lasfly.wav        redvulnerable.wav  w_pkup.wav
blue_returned.wav   menu1.wav        red_wins_ctf.wav

./trunk/data1/sound/misc/cow:
groan.wav  moo.wav  step1.wav

./trunk/data1/sound/music:
cp-ribeye.ogg  dm-eternal.ogg    dm-redred.ogg       menumusic.ogg
dm-deimos.ogg  dm-frontier.ogg    dm-saucer.ogg
dm-dismal.ogg  dm-horus.ogg    dm-turbo.ogg
dm-dynamo.ogg  dm-inferno.ogg    dm-warmachine.ogg

./trunk/data1/sound/player:
burn1.wav   fall1.wav  jump1.wav    male       step_metal1.wav    wade2.wav
burn2.wav   fall2.wav  land1.wav    step1.wav  step_metal2.wav    wade3.wav
death1.wav  fry.wav    lava1.wav    step2.wav  step_metal3.wav    watr_in.wav
death4.wav  gasp1.wav  lava2.wav    step3.wav  step_metal4.wav    watr_out.wav
drown1.wav  gasp2.wav  lava_in.wav  step4.wav  wade1.wav    watr_un.wav

./trunk/data1/sound/player/male:
bump1.wav   death4.wav    gurp1.wav      pain100_2.wav  pain50_2.wav
death1.wav  drown1.wav    gurp2.wav      pain25_1.wav   pain75_1.wav
death2.wav  fall1.wav    jump1.wav      pain25_2.wav   pain75_2.wav
death3.wav  fall2.wav    pain100_1.wav  pain50_1.wav

./trunk/data1/sound/smallmech:
sight.wav

./trunk/data1/sound/taunts:
commander  enforcer  lauren  martiancyborg  martianenforcer  slashbot

./trunk/data1/sound/taunts/commander:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/enforcer:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/lauren:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/martiancyborg:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/martianenforcer:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/taunts/slashbot:
taunt1.wav  taunt2.wav    taunt3.wav  taunt4.wav    taunt5.wav

./trunk/data1/sound/vehicles:
bomberidle.wav     flybomb.wav  shootbomb.wav   warning.wav
explodebomb.wav  got_in.wav   shootlaser.wav

./trunk/data1/sound/weapons:
biglaser.wav     grenlf1a.wav  machgf2b.wav  rocklr1b.wav
blastf1a.wav     grenlr1b.wav  machgf3b.wav  rocklx1a.wav
clank.wav     grenlx1a.wav  machgf4b.wav  shotgf1b.wav
clink01.wav     hypbrl1a.wav  machgf5b.wav  smartgun_hum.wav
clink02.wav     hyprbf1a.wav  noammo.wav    vaporizer_hum.wav
electroball.wav  lightoff.wav  railgf1a.wav  viofire1.wav
energyfield.wav  lighton.wav   rockfly.wav   viofire2.wav
grenlb1b.wav     machgf1b.wav  rocklf1a.wav  whoosh.wav

./trunk/data1/sound/world:
botwon.wav    electricity.wav  jumppad1.wav  ric1.wav    steam1.wav
button1.wav    explosion1.wav     laser1.wav    ric2.wav    steam2.wav
button2.wav    explosion2.wav     platstop.wav  ric3.wav    turbine1.wav
distantjet.wav    hyprbf1a.wav     rcktfly.wav   rocket.wav  youwin.wav

./trunk/data1/textures:
alien     arena5      common        metal        ramp1c.wal    ramp1f.wal
arena1     arena6      cr3blankclear.wal    null.tga    ramp1d.tga    ramp1.tga
arena10  arena7      dalek        rage        ramp1d.wal    ramp1.wal
arena2     arena8      evil        ramp1b.tga  ramp1e.tga    water
arena3     arena9      forsaken        ramp1b.wal  ramp1e.wal    xempx
arena4     billboards  martian        ramp1c.tga  ramp1f.tga

./trunk/data1/textures/alien:
support5.tga

./trunk/data1/textures/arena1:
jpad1a.tga  jpad1d.wal          metalbrick3c.tga    o3arch1.tga    o3bricks6.tga
jpad1a.wal  jpad1e.tga          metalbrick3d.tga    o3bricks12.tga    o3bricks.tga
jpad1b.tga  jpad1e.wal          metalbrick4a.tga    o3bricks21.tga    o3ice1.tga
jpad1b.wal  metalbrick1.tga   metalbrick4b.tga    o3bricks22.tga    o3ice2.tga
jpad1c.tga  metalbrick2.tga   metalbrick4c.tga    o3bricks23.tga    o3ice3.tga
jpad1c.wal  metalbrick3a.tga  metalbrick4d.tga    o3bricks2.tga    o3ice4.tga
jpad1d.tga  metalbrick3b.tga  metalbrick5.tga    o3bricks3.tga    o3rocks1.tga

./trunk/data1/textures/arena10:
bricks1_nm.tga      building6_nm.tga    container1.tga       pipes1.tga
bricks1.tga      building6.tga        container2_hm.tga  rockdirt1_hm.tga
bricks2_hm.tga      building7_nm.tga    container2_nm.tga  rockdirt1ng_hm.tga
bricks2_nm.tga      building7.tga        container2.tga       rockdirt1ng_nm.tga
bricks2.tga      building8_nm.tga    container3_hm.tga  rockdirt1ng.tga
bricks3.tga      building8.tga        container3_nm.tga  rockdirt1_nm.tga
building10.tga      building9_nm.tga    container3.tga       rockdirt1.tga
building1_nm.tga  building9.tga        container4_hm.tga  sewergrate1_nm.tga
building1.tga      cement1.tga        container4_nm.tga  sewergrate1.tga
building2_nm.tga  cobblestone_hm.tga    container4.tga       sign1.tga
building2.tga      cobblestoneng_hm.tga    heap1_nm.tga       sign2.tga
building3_nm.tga  cobblestoneng_nm.tga    heap1.tga       sign3.tga
building3.tga      cobblestoneng.tga    neonsign1.tga       sign4.tga
building4_nm.tga  cobblestone_nm.tga    neonsign2.tga       sign5.tga
building4.tga      cobblestone.tga    neonsign3.tga       sign6.tga
building5_nm.tga  container1_hm.tga    neonsign4.tga
building5.tga      container1_nm.tga    neonsign5.tga

./trunk/data1/textures/arena2:
grid2.tga  gridb.tga  gride.tga    metal1.tga  metal4.tga
grid3.tga  gridc.tga  lava_nm.tga  metal2.tga  metal5.tga
grida.tga  gridd.tga  lava.tga       metal3.tga  metal6.tga

./trunk/data1/textures/arena3:
acceleratora.tga  acceleratorf.wal  light1.tga    orbe.wal       wall1.tga
acceleratora.wal  acceleratorg.tga  light2.tga    orbf.tga       wall2.tga
acceleratorb.tga  acceleratorg.wal  orba.tga    orbf.wal       wall3.tga
acceleratorb.wal  ceiling1.tga        orba.wal    orbg.tga       wall4.tga
acceleratorc.tga  ceiling2.tga        orbb.tga    orbg.wal       wall5.tga
acceleratorc.wal  door1.tga        orbb.wal    orbh.tga       water_nm.tga
acceleratord.tga  floor1.tga        orbc.tga    orbh.wal       water.tga
acceleratord.wal  floor2_nm.tga     orbc.wal    trim1.tga
acceleratore.tga  floor2.tga        orbd.tga    trim2.tga
acceleratore.wal  floor3.tga        orbd.wal    trimlite1.tga
acceleratorf.tga  floor4.tga        orbe.tga    trimlite2.tga

./trunk/data1/textures/arena4:
bricks1_nm.tga    floor1.cpt     floor3_nm.tga  light3.tga       wall1_nm.tga
bricks1.tga    floor1_nm.tga  floor3.tga     support1_nm.tga  wall1.tga
comp1_nm.tga    floor1.tga     light1.tga     support1.tga     wall2_nm.tga
comp1.tga    floor2.tga     light2.tga     support2.tga     wall2.tga

./trunk/data1/textures/arena5:
bast1_nm.tga      egypt2.tga      light1.tga  lighte.tga      o3win12.tga
bast1.tga      egypt3.tga      light2.tga  lighte.wal      rock2_nm.tga
bast2.tga      egypt4.tga      lighta.tga  lightf.tga      rock2.tga
bricks4_1_nm.tga  egypt5.tga      lighta.wal  lightf.wal      rock_3b_nm.tga
bricks4_1.tga      egypt6_nm.tga   lightb.tga  o3cath11.tga    rock_3b.tga
cave_nm.tga      egypt6.tga      lightb.wal  o3cath3.tga     sekhmet3.tga
cave.tga      egypt7.tga      lightc.tga  o3cath5.tga     trim_nm.tga
chain.tga      fod.tga      lightc.wal  o3cath8.tga     trim_sm.tga
cobweb.tga      ground1_nm.tga  lightd.tga  o3rock5_nm.tga  trim.tga
egypt1.tga      ground1.tga      lightd.wal  o3rock5.tga

./trunk/data1/textures/arena6:
alienarena2.tga  ctfwinred.tga      icerock.tga     plate4.tga      skullite.tga
alienarena.tga     flamejet.tga      ice.tga     plate5_nm.tga      skull_nm.tga
blacktrans.tga     flare.tga      plate1_nm.tga  plate5_sm.tga      skull.tga
bricks1_hm.tga     fodblue.tga      plate1.tga     plate5.tga      snow_nm.tga
bricks1_nm.tga     girder1.tga      plate2_nm.tga  rimlight2.tga      snow.tga
bricks1_sm.tga     girder2.tga      plate2.tga     rimlight.tga      tech1.tga
bricks1.tga     icerock2_nm.tga  plate3_nm.tga  rings.tga      wires1.tga
city20.tga     icerock2.tga      plate3.tga     skullite_hm.tga
ctfwinblue.tga     icerock_nm.tga   plate4_nm.tga  skullite_nm.tga

./trunk/data1/textures/arena7:
bluegrid.tga   light1.tga     redgrid.tga    tekwall4.tga
ceiling1.tga   light2.tga     tekfloor1_nm.tga    tekwall5_nm.tga
floor1_hm.tga  light3.tga     tekfloor1.tga    tekwall5.tga
floor1_nm.tga  light4.tga     tekwall1_nm.tga    tekwall6_nm.tga
floor1.tga     light5.tga     tekwall1.tga    tekwall6.tga
floor2_hm.tga  light6.tga     tekwall2_nm.tga    tekwall7_nm.tga
floor2_nm.tga  light7.tga     tekwall2.tga    tekwall7.tga
floor2.tga     light8.tga     tekwall3_hm.tga    tekwall8_nm.tga
glass.tga      light9.tga     tekwall3_nm.tga    tekwall8.tga
grate1.tga     lightgid2.tga  tekwall3r_hm.tga    tekwall9_hm.tga
light10.tga    lightgid.tga   tekwall3r_nm.tga    tekwall9_nm.tga
light11.tga    metal1.tga     tekwall3r.tga    tekwall9.tga
light12.tga    metal2_nm.tga  tekwall3.tga    warning.tga
light13.tga    metal2.tga     tekwall4_nm.tga
light14.tga    metal3.tga     tekwall4r_nm.tga
light1r.tga    piston1.tga    tekwall4r.tga

./trunk/data1/textures/arena8:
bark1_hm.tga         crackedrock1.tga      floor3_hm.tga      metaltrim2_hm.tga
bark1_nm.tga         crackedrock2_hm.tga  floor3_nm.tga      metaltrim2_nm.tga
bark1.tga         crackedrock2_nm.tga  floor3.tga         metaltrim2.tga
barnroof_nm.tga      crackedrock2.tga      floor4_hm.tga      rock1_nm.tga
barnroof.tga         crackedrock3_hm.tga  floor4_nm.tga      rock1.tga
barnwindows.tga      crackedrock3_nm.tga  floor4.tga         roughwood_nm.tga
barnwood2_nm.TGA     crackedrock3.tga      grass2_nm.tga      roughwood.tga
barnwood2.tga         crackedrock4_hm.tga  grass2.tga         sand1.tga
barnwood_nm.tga      crackedrock4_nm.tga  grate1.tga         sand2.tga
barnwood.tga         crackedrock4.tga      ice.tga         slime_nm.tga
blackbrick1.tga      egyptbrick1_hm.tga   lavalmetal_nm.tga  slime.tga
blackbrick2.tga      egyptbrick1_nm.tga   lavalmetal.tga     snow_hm.tga
blackbrick3.tga      egyptbrick1.tga      leaves1.tga         snow_nm.tga
brickwall1_hm.tga    egyptfloor1_nm.tga   metal1_nm.tga      snow.tga
brickwall1_nm.tga    egyptfloor1.tga      metal1.tga         stonefloor1_hm.tga
brickwall1.tga         egyptrock1_hm.tga      metalroof_hm.tga   stonefloor1_nm.tga
cinderblocks_hm.tga  egyptrock1_nm.tga      metalroof_nm.tga   stonefloor1.tga
cinderblocks_nm.tga  egyptrock1.tga      metalroof.tga      wood1_hm.tga
cinderblocks.tga     egyptrock2_nm.tga      metaltrim1_hm.tga  wood1_nm.tga
crackedrock1_hm.tga  egyptrock2.tga      metaltrim1_nm.tga  wood1.tga
crackedrock1_nm.tga  fern.tga          metaltrim1.tga

./trunk/data1/textures/arena9:
beam_metal_nm.tga      icemetal1_nm.tga        panel3.tga
beam_metal.tga           icemetal1.tga           panel4_hm.tga
biggrate1_hm.tga       icemetal2_hm.tga        panel4_nm.tga
biggrate1_nm.tga       icemetal2_nm.tga        panel4.tga
biggrate1.tga           icemetal2.tga           panel5_nm.tga
boxmetal_hm.tga        iceplate_nm.tga           panel5.tga
boxmetal_nm.tga        iceplate.tga           platefloor1_hm.tga
boxmetal.tga           icetrim1_hm.tga           platefloor1_nm.tga
brokencement1_nm.tga   icetrim1_nm.tga           platefloor1.tga
brokencement1.tga      icetrim1.tga           platefloor2_hm.tga
cable1.tga           icetrim2_hm.tga           platefloor2_nm.tga
cable2.tga           icetrim2_nm.tga           platefloor2.tga
cable3.tga           icetrim2.tga           platefloor3_hm.tga
cable4.tga           icewall1_hm.tga           platefloor3_nm.tga
cementwall1_hm.tga     icewall1_nm.tga           platefloor3.tga
cementwall1_nm.tga     icewall1.tga           platefloor4_hm.tga
cementwall1.tga        icicles.tga           platefloor4_nm.tga
chainlinkfence.tga     lightwhite.tga           platefloor4.tga
circuitwall1_hm.jpg    metal1_nm.tga           platefloor5_hm.tga
circuitwall1_nm.jpg    metal1.tga           platefloor5_nm.tga
circuitwall1_nm.tga    metal2_nm.tga           platefloor5.tga
circuitwall1.tga       metal2.tga           platefloor6_hm.tga
comppanel2.tga           metal3_nm.tga           platefloor6_nm.tga
comppanel.tga           metal3.tga           platefloor6.tga
dmpltfloor1_hm.tga     metal4_nm.tga           platefloor7_hm.tga
dmpltfloor1_nm.tga     metal4.tga           platefloor7_nm.tga
dmpltfloor1.tga        metal5_nm.tga           platefloor7.tga
factorybricks1_hm.tga  metal5.tga           platefloor8_hm.tga
factorybricks1_nm.tga  metal6_nm.tga           platefloor8_nm.tga
factorybricks1_sm.tga  metal6.tga           platefloor8.tga
factorybricks1.tga     metalfloor1_hm.tga      redwall1_nm.tga
floor1_nm.tga           metalfloor1_nm.tga      redwall1.tga
floor1.tga           metalfloor1.tga           roundlight.tga
floor2_nm.tga           metalgrate1.tga           rustmetal1_nm.tga
floor2.tga           metalhole.tga           rustmetal1.tga
floor3_hm.tga           metalplate1_nm.tga      techfloor1_hm.tga
floor3_nm.tga           metalplate1.tga           techfloor1_nm.tga
floor3.tga           metalscale_hm.tga       techfloor1.tga
grate1_nm.tga           metalscale_nm.tga       techwall1_hm.tga
grate1.tga           metalscale.tga           techwall1_nm.tga
grate2.tga           metaltilefloor1_hm.tga  techwall1.tga
grate3.tga           metaltilefloor1_nm.tga  techwall2_hm.tga
greenfloor_nm.tga      metaltilefloor1.tga     techwall2_nm.tga
greenfloor.tga           metaltrim1.tga           techwall2.tga
greenglass.tga           metalwall1_hm.tga       techwall3_hm.tga
greenmetal_nm.tga      metalwall1_nm.tga       techwall3_nm.tga
greenmetal.tga           metalwall1.tga           techwall3.tga
greenwall1_nm.tga      metalwall2_hm.tga       trim1_nm.tga
greenwall1.tga           metalwall2_nm.tga       trim1.tga
greenwall2_hm.tga      metalwall2.tga           trim2_nm.tga
greenwall2_nm.tga      metalwall3_hm.tga       trim2.tga
greenwall2.tga           metalwall3_nm.tga       wall1_nm.tga
greenwall3_nm.tga      metalwall3.tga           wall1.tga
greenwall3.tga           metalwall4_hm.tga       wall2_hm.tga
greenwall4_nm.tga      metalwall4_nm.tga       wall2_nm.tga
greenwall4.tga           metalwall4.tga           wall2.tga
greenwall5_hm.jpg      metalwall5_hm.tga       weapongrate.tga
greenwall5_nm.tga      metalwall5_nm.tga       wetbricks1_hm.tga
greenwall5.tga           metalwall5.tga           wetbricks1_nm.tga
greenwall6_nm.tga      metalwall6_hm.tga       wetbricks1.tga
greenwall6.tga           metalwall6_nm.tga       wires1.tga
hexfloor1_hm.tga       metalwall6.tga           wires2.tga
hexfloor1_nm.tga       metalwall7_hm.tga       wires3.tga
hexfloor1.tga           metalwall7_nm.tga       wires4.tga
hexfloor2_hm.tga       metalwall7.tga           wires5.tga
hexfloor2_nm.tga       metalwall8_hm.tga       wires6.tga
hexfloor2.tga           metalwall8_nm.tga       wires7.tga
hexglass.tga           metalwall8.tga           wires8.tga
hexgratefloor_hm.tga   panel1_nm.tga           yellowmetal_nm.tga
hexgratefloor_nm.tga   panel1.tga           yellowmetal.tga
hexgratefloor.tga      panel2_nm.tga           yellowwall1_hm.jpg
icefloor1_nm.tga       panel2.tga           yellowwall1_nm.tga
icefloor1.tga           panel3_hm.tga           yellowwall1.tga
icemetal1_hm.tga       panel3_nm.tga

./trunk/data1/textures/billboards:
billboard1.tga    billboard2.tga    billboard3.tga    billboard4.tga

./trunk/data1/textures/common:
0_clip.tga    caulk.tga      hint.tga        nolightmap.tga    trigger.tga
0_hint.tga    clip.tga       missileclip.tga    origin.tga    weapclip.tga
0_sky1.tga    cushion.tga    nodraw.tga    qer_portal.tga    white.tga
areaportal.tga    full_clip.tga  nodrop.tga    slick.tga

./trunk/data1/textures/dalek:
column1.tga   floor2.tga  floor4.tga  wall2.tga  wall4.tga  wall6.tga
console1.tga  floor3.tga  wall1.tga   wall3.tga  wall5.tga  wall7.tga

./trunk/data1/textures/evil:
confllrtile2pad_nm.tga    e8warning_nm.tga       steptop_mtl2_nm.tga
confllrtile2pad.tga    e8warning.tga           steptop_mtl2.tga
drktek_symb_hm.tga    stepside_mtl2_hm.tga       steptop_mtl3_hm.tga
drktek_symb_nm.tga    stepside_mtl2_nm.tga       steptop_mtl3_nm.tga
drktek_symb.tga        stepside_mtl2.tga       steptop_mtl3.tga
e6basegrate_nm.tga    stepside_mtl3_hm.tga       techallmix_hm.tga
e6basegrate.tga        stepside_mtl3_nm.tga       techallmix_nm.tga
e6dtrimnd_nm.tga    stepside_mtl3.tga       techallmix.tga
e6dtrimnd.tga        stepside_mtl4light_hm.tga  trim_drkmtl_nm.tga
e6launchengine_hm.tga    stepside_mtl4light_nm.tga  trim_drkmtl.tga
e6launchengine_nm.tga    stepside_mtl4light.tga       trimrstmtlpipes_nm.tga
e6launchengine.tga    stepside_mtl5_nm.tga       trimrstmtlpipes.tga
e6supptrim128.tga    stepside_mtl5.tga       trstmtl_panelbig_hm.tga
e6trim_basic128_nm.tga    stepside_mtl_nm.tga       trstmtl_panelbig_nm.tga
e6trim_basic128.tga    stepside_mtl.tga       trstmtl_panelbig.tga
e8warning_hm.tga    steptop_mtl2_hm.tga

./trunk/data1/textures/forsaken:
glass.tga

./trunk/data1/textures/martian:
biometal1_hm.tga  glass1.tga     metal3.tga          shiphull_hm.tga
biometal1_nm.tga  grass.tga     metal4.tga          shiphull_nm.tga
biometal1.tga      grass_tga.tga  metal5.tga          shiphull.tga
chains.tga      light1.tga     metalrings1.tga      skytrees.tga
coiledwire.tga      light2.tga     metalrings2.tga      skytrees_tga.tga
console1.tga      light3.tga     ribtubeswirl_hm.jpg  tree2_tga.tga
console2.tga      light4.tga     ribtubeswirl_nm.jpg  tree_bottom.tga
console3.tga      light5.tga     ribtubeswirl.tga     tree_bottom_tga.tga
console4.tga      light6.tga     shiphull2_hm.tga     tree_tga.tga
floor1.tga      metal1.tga     shiphull2_nm.tga     tree_top.tga
floor2.tga      metal2.tga     shiphull2.tga          tree_top_tga.tga

./trunk/data1/textures/metal:
bigconduit.tga    light2_s.tga    metal2.tga    silo.tga      wall2.tga
ceiling1.tga    light2.tga    metal3.tga    smallconduit.tga  wall3.tga
door1.tga    light3_s.tga    metal4.tga    trim1.tga      wall4.tga
doorjam.tga    light3.tga    metal5.tga    trim2.tga      wall5.tga
fade1.tga    light4.tga    openfloor2.tga    wall1_nm.tga      wall6.tga
fade2.tga    light5_s.tga    openfloor.tga    wall1_sm.tga      walllite.tga
floor.tga    light5.tga    plat.tga    wall1.tga
light1_s.tga    medconduit.tga    saucer1.tga    wall2_nm.tga
light1.tga    metal1.tga    saucer2.tga    wall2_sm.tga

./trunk/data1/textures/rage:
beam_purple_hm.tga  hexfloor_hm.tga   metallight_2.tga
beam_purple_nm.tga  hexfloor_nm.tga   metal_panel.tga
beam_purple.tga     hexfloor_red.tga  rimlightpurple.tga
ceiling2_nm.tga     hexfloor.tga      support_beam.tga
ceiling2.tga        jpad1a.tga          support_column_hm.tga
ceiling_nm.tga        lava.tga          support_column_nm.tga
ceiling.tga        light10.tga       support_column.tga
floor2.tga        light12.tga       support_trim.tga
floor5.tga        light1.tga          trimlight_purple.tga
fod1.tga        light5.tga          trimlight_red.tga
grid1.tga        light7.tga          wall_blue.tga
hexfloor_blue.tga   light8.tga

./trunk/data1/textures/water:
bluewater_nm.tga  bluewater.tga  clearwater_nm.tga  clearwater.tga  waterpx.tga

./trunk/data1/textures/xempx:
a3light1b.tga  a7light10.wal  a7light2.tga  a9metal5.tga
a6bt.tga       a7light1b.tga  a7light3.tga  light1.tga
a7light10.tga  a7light1.tga   a7light4.tga  lightbeam1.tga

./trunk/data1/vehicles:
bomber    deathball  hover  strafer

./trunk/data1/vehicles/bomber:
bomb.md2  console_normal.tga  helmet.md2       skin.tga  v_wep.md2
bomb.tga  console.tga          skin_normal.tga  tris.md2  window.md2

./trunk/data1/vehicles/deathball:
deathball.md2  deathmask.tga    skin.tga
deathball.tga  skin_normal.tga    v_wep.md2

./trunk/data1/vehicles/hover:
console_normal.tga  flames.md2    skin_normal.tga  v_wep.md2
console.tga        skin.jpg    tris.md2     window.md2

./trunk/data1/vehicles/strafer:
console_normal.tga  skin_normal.tga  tris.md2    window.md2
console.tga        skin.tga         v_wep.md2

./trunk/docs:
AA\ Dutch.txt    AA\ German.txt       AA\ Italian.txt     AA\ Russian.txt
AA_ES.txt    AA\ Greek.txt       AA\ Polish.txt      license.txt
AA\ French.txt    AA\ Hungarian.txt  AA\ Portuguese.txt  README.txt

./trunk/source:
client         codered.sln     Makefile  ref_gl    unix
codered.dsp  codered.vcproj  null      release    utils3
codered.dsw  game         qcommon   server    win32

./trunk/source/client:
adivtab.h  cl_input.c  cl_tent.c  keys.h      qmenu.c        vid.h
anorms.h   cl_inv.c    cl_view.c  menu.c      qmenu.h        vid_menu.c
cl_cin.c   cl_main.c   console.c  mpg123.h    ref.h        x86.c
cl_ents.c  cl_newfx.c  console.h  mpglib.h    screen.h
cl_fx.c    cl_parse.c  curl      mpglib.lib  snd_file.c
cl_http.c  cl_pred.c   input.h      qal.c       snd_openal.c
client.h   cl_scrn.c   keys.c      qal.h       sound.h

./trunk/source/client/curl:
curl.h       easy.h    mprintf.h  stdcheaders.h
curlver.h  libcurl.lib    multi.h    types.h

./trunk/source/game:
acesrc      game.vcproj     g_items.c    g_spawn.c     g_weapon.c    p_weapon.c
c_cam.c   g_chase.c     g_local.h    g_svcmds.c    m_move.c    q_shared.c
cow.c      g_cmds.c     g_main.c     g_target.c    m_player.h    q_shared.h
cow.h      g_combat.c     g_misc.c     g_trigger.c   p_client.c
g_ai.c      g_ctf.c     g_monster.c  g_unlagged.c  p_hud.c
game.def  g_deathball.c  g_phys.c     g_utils.c     p_trail.c
game.h      g_func.c     g_save.c     g_vehicles.c  p_view.c

./trunk/source/game/acesrc:
acebot_ai.c       acebot_config.cpp  acebot_movement.c
acebot_cmds.c       acebot.h          acebot_nodes.c
acebot_compress.c  acebot_items.c     acebot_spawn.c

./trunk/source/null:
cl_null.c     in_null.c      swimp_null.c  vid_null.c
glimp_null.c  snddma_null.c  sys_null.c

./trunk/source/qcommon:
cmd.c      common.c  crc.h   files.c   net_chan.c  qcommon.h
cmodel.c  crc.c     cvar.c  mdfour.c  pmove.c      qfiles.h

./trunk/source/ref_gl:
anorms.h    r_draw.c   r_mapscript.cpp    r_model.h     r_varray.c
anormtab.h  r_image.c  r_math.c        r_postprocess.c  r_vlights.c
glext.h     r_image.h  r_math.h        r_script.c     r_warp.c
jpeg        r_light.c  r_mesh.c        r_script.h     vlights.h
qgl.h        r_local.h  r_misc.c        r_shadows.c     warpsin.h
r_bloom.c   r_main.c   r_model.c    r_surf.c

./trunk/source/ref_gl/jpeg:
jconfig.h  jmorecfg.h  jpeglib.h

./trunk/source/release:
arena  client  crded  ded  game  game.so  ref_gl

./trunk/source/release/arena:
acebot_ai.o       cow.o      g_func.o     g_svcmds.o    p_client.o
acebot_cmds.o       g_ai.o      g_items.o    g_target.o    p_hud.o
acebot_compress.o  game.so      g_main.o     g_trigger.o   p_trail.o
acebot_items.o       g_chase.o      g_misc.o     g_unlagged.o  p_view.o
acebot_movement.o  g_cmds.o      g_monster.o  g_utils.o     p_weapon.o
acebot_nodes.o       g_combat.o      g_phys.o     g_vehicles.o  q_shared.o
acebot_spawn.o       g_ctf.o      g_save.o     g_weapon.o
c_cam.o           g_deathball.o  g_spawn.o    m_move.o

./trunk/source/release/client:
cl_cin.o    cl_parse.o    console.o  net_chan.o  rw_unix.o     sv_send.o
cl_ents.o   cl_pred.o    crc.o       net_udp.o   snd_file.o    sv_user.o
cl_fx.o     cl_scrn.o    cvar.o       pmove.o     snd_openal.o  sv_world.o
cl_http.o   cl_tent.o    files.o    qal.o       sv_ccmds.o    sys_unix.o
cl_input.o  cl_view.o    glob.o       qal_unix.o  sv_ents.o     vid_menu.o
cl_inv.o    cmd.o    keys.o       qmenu.o     sv_game.o     vid_so.o
cl_main.o   cmodel.o    mdfour.o   q_shared.o  sv_init.o
cl_newfx.o  common.o    menu.o       q_shunix.o  sv_main.o

./trunk/source/release/ded:
cl_null.o  crc.o    mdfour.o    q_shared.o  sv_game.o  sv_user.o
cmd.o       cvar.o   net_chan.o    q_shunix.o  sv_init.o  sv_world.o
cmodel.o   files.o  net_udp.o    sv_ccmds.o  sv_main.o  sys_unix.o
common.o   glob.o   pmove.o    sv_ents.o   sv_send.o

./trunk/source/release/game:
acebot_ai.o       cow.o      g_items.o    g_target.o    p_hud.o
acebot_cmds.o       g_ai.o      g_main.o     g_trigger.o   p_trail.o
acebot_compress.o  g_chase.o      g_misc.o     g_unlagged.o  p_view.o
acebot_items.o       g_cmds.o      g_monster.o  g_utils.o     p_weapon.o
acebot_movement.o  g_combat.o      g_phys.o     g_vehicles.o  q_shared.o
acebot_nodes.o       g_ctf.o      g_save.o     g_weapon.o
acebot_spawn.o       g_deathball.o  g_spawn.o    m_move.o
c_cam.o           g_func.o      g_svcmds.o   p_client.o

./trunk/source/release/ref_gl:
gl_glx.o    r_draw.o   r_main.o  r_misc.o      r_script.o   r_varray.o
qgl_unix.o  r_image.o  r_math.o  r_model.o      r_shadows.o  r_vlights.o
r_bloom.o   r_light.o  r_mesh.o  r_postprocess.o  r_surf.o     r_warp.o

./trunk/source/server:
server.h    sv_ents.c  sv_init.c  sv_null.c  sv_user.c
sv_ccmds.c  sv_game.c  sv_main.c  sv_send.c  sv_world.c

./trunk/source/unix:
gl_glx.c  glob.h      net_udp.c   qasm.h      q_shunix.c  rw_unix.h   vid_so.c
glob.c      glw_unix.h  qal_unix.c  qgl_unix.c  rw_unix.c   sys_unix.c

./trunk/source/utils3:
bsp  common  Makefile

./trunk/source/utils3/bsp:
bsp.dsp  bsp.dsw  bspinfo3  bsp.ncb  bsp.opt  qbsp3  qrad3  qvis3

./trunk/source/utils3/bsp/bspinfo3:
bspinfo3.c  bspinfo3.dsp

./trunk/source/utils3/bsp/qbsp3:
brushbsp.c  glfile.c    portals.c  qbsp3.plg    textures.c
csg.c        leakfile.c    prtfile.c  qbsp.h    tree.c
faces.c     map.c    qbsp3.c    resource.h    writebsp.c
gldraw.c    nodraw.c    qbsp3.dsp  resource.rc

./trunk/source/utils3/bsp/qrad3:
lightmap.c  qrad3.c    qrad3.dsw  qrad.h
patches.c   qrad3.dsp  qrad3.plg  trace.c

./trunk/source/utils3/bsp/qvis3:
flow.c    qvis3.c  qvis3.dsp  qvis3.plg  qvis3_res.rc  resource.h  vis.h

./trunk/source/utils3/common:
bspfile.c  l3dslib.c  mathlib.c  memory.h    polylib.h     threads.c
bspfile.h  l3dslib.h  mathlib.h  parsecfg.c  qfiles.h     threads.h
cmdlib.c   lbmlib.c   md4.c     parsecfg.h  scriplib.c  trilib.c
cmdlib.h   lbmlib.h   memory.c     polylib.c   scriplib.h  trilib.h

./trunk/source/win32:
conproc.c  glw_win.h  net_wins.c  qal_win.c  resource.h  vid_dll.c
conproc.h  in_win.c   Q2.ico      qgl_win.c  snd_win.c     winquake.h
glw_imp.c  lib          q2.rc      q_shwin.c  sys_win.c

./trunk/source/win32/lib:
libjpeg.lib          libvorbis_static.lib    vorbisfile_static.lib
libogg_static.lib      ogg_static.lib    vorbis_static.lib
libvorbisfile_static.lib  vorbisenc_static.lib

./trunk/Tools:
aaradiant.exe  galaxy              Master\ Server  projects       web
defaults       LinuxScripts          prefabs          RubyBrowser  WinInstall
FUSE           Map\ compiling\ tools  PrefabScripts   statsgen

./trunk/Tools/defaults:
entities.def

./trunk/Tools/FUSE:
BUILDING.TXT  fuse.cbp      fuse.workspace      main.c     offline
config          fuse.exe      fuse.xcf          Makefile     slink.c
config.c      fuse.glade  global.h          models.c     slink.h
config.h      fuse.ico      iconv.dll          models.h
COPYING.TXT   fuse.rc      libglade-2.0-0.dll  NOTES.TXT

./trunk/Tools/FUSE/config:
games.xml

./trunk/Tools/FUSE/offline:
189.12.189.10-16574.udp  69.143.97.41-27920.udp
189.13.7.43-27910.udp     69.143.97.41-27970.udp
190.55.10.13-27910.udp     70.233.170.106-27910.udp
24.208.244.91-62753.udp  72.129.166.209-27910.udp
24.208.244.91-62754.udp  84.3.11.220-27910.udp
24.208.244.91-62755.udp  87.117.201.24-27920.udp
61.82.45.170-27910.udp     87.117.201.24-27930.udp
68.228.24.233-27910.udp  87.117.201.24-27940.udp
68.61.124.10-27930.udp     87.117.201.24-27950.udp
69.14.111.12-27910.udp     master2.corservers.com-27900.udp
69.143.97.41-27910.udp     master.corservers.com-27900.udp

./trunk/Tools/galaxy:
buddylist.db   Galaxy.dsw      PollServer.cpp           Socket.h
BuddyName.cpp  Galaxy.h          PollServer.h               Startup.cpp
BuddyName.h    Galaxy.plg      ReadMe.txt               Startup.h
fce32.dll      Galaxy.rc      res                   StdAfx.cpp
fce32.lib      hyperlink.cpp      resource.h               StdAfx.h
fce.h           hyperlink.h      SkinHeaderCtrl.cpp           UpdateDlg.cpp
Functions.cpp  keycode.h      SkinHeaderCtrl.h           UpdateDlg.h
Functions.h    MEMDC.H          SkinHorizontalScrollbar.cpp  UpdateGame.cpp
Galaxy.aps     mfcpp.cpp      SkinHorizontalScrollbar.h    userinfo.h
Galaxy.clw     mfcpp.h          SkinListCtrl.cpp           windebug.cpp
Galaxy.cpp     minmaxlogic.cpp      SkinListCtrl.h           windebug.h
GalaxyDlg.cpp  minmaxlogic.h      SkinVerticleScrollbar.cpp
GalaxyDlg.h    PlayerProfile.cpp  SkinVerticleScrollbar.h
Galaxy.dsp     PlayerProfile.h      Socket.cpp

./trunk/Tools/galaxy/res:
bitmap10.bmp  bitmap28.bmp             HorizontalScrollBarThumb.bmp
bitmap11.bmp  bitmap29.bmp             icon10.ico
bitmap12.bmp  bitmap2.bmp             icon11.ico
bitmap13.bmp  bitmap3.bmp             icon12.ico
bitmap14.bmp  bitmap4.bmp             icon1.ico
bitmap15.bmp  bitmap5.bmp             icon2.ico
bitmap16.bmp  bitmap6.bmp             icon3.ico
bitmap17.bmp  bitmap7.bmp             icon5.ico
bitmap18.bmp  bitmap8.bmp             icon6.ico
bitmap19.bmp  bitmap9.bmp             icon7.ico
bitmap1.bmp   ColumnHeaderEnd.bmp         ListCtrl_Tile.bmp
bitmap20.bmp  ColumnHeaderSpan.bmp         logo_big_02.bmp
bitmap21.bmp  ColumnHeaderStart.bmp         VerticleScrollbarBottom.bmp
bitmap22.bmp  computer.ico             VerticleScrollBarDownArrow.bmp
bitmap23.bmp  Galaxy.ico             VerticleScrollBarSpan.bmp
bitmap24.bmp  Galaxy.rc2             VerticleScrollBarThumb.bmp
bitmap25.bmp  HorizontalScrollBarLeftArrow.bmp     VerticleScrollbarTop.bmp
bitmap26.bmp  HorizontalScrollBarRightArrow.bmp  VerticleScrollBarUpArrow.bmp
bitmap27.bmp  HorizontalScrollBarSpan.bmp

./trunk/Tools/LinuxScripts:
check-configs  kill-runaway-crded  launchservers  rcon      svstat
check-master   launch-server       randomgravity  README

./trunk/Tools/Map compiling tools:
2007  2008

./trunk/Tools/Map compiling tools/2007:
qbsp3.exe  qrad3.exe  qvis3.exe

./trunk/Tools/Map compiling tools/2008:
qbsp3.exe  qrad3.exe  qvis3.exe

./trunk/Tools/Master Server:
CR\ Master.dsp    CR\ Master.dsw    crmaster.exe  master.c

./trunk/Tools/prefabs:
aasign.pfb       furnace.pfb    pillar2.pfb    skull.pfb     support9.pfb
archway1.pfb       hall1.pfb    pillar3.pfb    stairs.pfb    teleporter.pfb
beamchain.pfb       jramp.pfb    pillar.pfb     support1.pfb  wall1.pfb
blueflagpad.pfb    lamp1.pfb    pipe1.pfb      support2.pfb  wall2.pfb
computer1.pfb       light1.pfb    platform1.pfb  support3.pfb  walllite.pfb
computer2.pfb       light2.pfb    radar.pfb      support4.pfb  weaponpad.pfb
dbgoal.pfb       light3.pfb    ramp1.pfb      support5.pfb
door2.pfb       light4.pfb    sbend.pfb      support6.pfb
door.pfb       light5.pfb    shall.pfb      support7.pfb
floatingskull.pfb  light6.pfb    skullight.pfb  support8.pfb

./trunk/Tools/PrefabScripts:
pipegen.rb  torus.rb  wc_to_aa.rb

./trunk/Tools/projects:
alienarena.qe4

./trunk/Tools/RubyBrowser:
browser.glade  browser.png  browser.rbw  debug    INSTALL.TXT

./trunk/Tools/RubyBrowser/debug:
189.12.189.10-16574.dmp  69.143.97.41-27920.dmp
189.13.7.43-27910.dmp     69.143.97.41-27970.dmp
190.55.10.13-27910.dmp     70.233.170.106-27910.dmp
24.208.244.91-62753.dmp  72.129.166.209-27910.dmp
24.208.244.91-62754.dmp  84.3.11.220-27910.dmp
24.208.244.91-62755.dmp  87.117.201.24-27920.dmp
61.82.45.170-27910.dmp     87.117.201.24-27930.dmp
68.228.24.233-27910.dmp  87.117.201.24-27940.dmp
68.61.124.10-27930.dmp     87.117.201.24-27950.dmp
69.14.111.12-27910.dmp     master.corservers.com-27900.dmp
69.143.97.41-27910.dmp

./trunk/Tools/statsgen:
fce32.dll  keycode.h   statsgen.cpp  statsgen.ncb  statstemplate.html
fce32.lib  ReadMe.txt  statsgen.dsp  statsgen.opt  StdAfx.cpp
fce.h       StatsGen    statsgen.dsw  statsgen.plg  StdAfx.h

./trunk/Tools/statsgen/StatsGen:
about.html   clan3.html       clanrank.html  stats10.html  stats7.html
backup         clan4.html       clans.db         stats11.html  stats8.html
bestof.html  clan5.html       global.html    stats1.html   stats9.html
clan0.html   clan6.html       index.html     stats2.html   statsgen.exe
clan10.html  clan7.html       menu.html      stats3.html   top.html
clan11.html  clan8.html       playerrank.db  stats4.html
clan1.html   clan9.html       poll.db         stats5.html
clan2.html   clanladder.html  sorted.db      stats6.html

./trunk/Tools/statsgen/StatsGen/backup:

./trunk/Tools/web:
adcode.txt  COPYING      INSTALL.TXT  rss        style.css
browser     dmflags.html  live           scan
config.php  index.html      remote.php   stats.mysql

./trunk/Tools/web/browser:
flags       healthcheck-master2.php  index.php  maps.php        servers.php
flags.php  healthcheck.php        ip_files   players.php    statfuncs.php
graph.php  img                maps       searchfuncs.php    support.php

./trunk/Tools/web/browser/flags:
A1.gif    BJ.gif    CZ.gif    GL.gif    JP.gif    MH.gif        NR.gif  SI.gif  UM.gif
A2.gif    BM.gif    DE.gif    GM.gif    KE.gif    MK.gif        NU.gif  SK.gif  US.gif
AD.gif    BN.gif    DJ.gif    GN.gif    KG.gif    ML.gif        NZ.gif  SL.gif  UY.gif
AE.gif    BO.gif    DK.gif    GP.gif    KH.gif    MM.gif        OM.gif  SM.gif  UZ.gif
AF.gif    BR.gif    DM.gif    GQ.gif    KI.gif    MN.gif        PA.gif  SN.gif  VA.gif
AG.gif    BS.gif    DO.gif    GR.gif    KM.gif    MO.gif        PE.gif  SO.gif  VC.gif
AI.gif    BT.gif    DZ.gif    GT.gif    KN.gif    MP.gif        PF.gif  SR.gif  VE.gif
AL.gif    BV.gif    EC.gif    GU.gif    KP.gif    MQ.gif        PG.gif  ST.gif  VG.gif
AM.gif    BW.gif    EE.gif    GW.gif    KR.gif    MR.gif        PH.gif  SV.gif  VI.gif
AN.gif    BY.gif    EG.gif    GY.gif    KW.gif    MS.gif        PK.gif  SY.gif  VN.gif
AO.gif    BZ.gif    ER.gif    HK.gif    KY.gif    MT.gif        PL.gif  SZ.gif  VU.gif
AP.gif    CA.gif    ES.gif    HM.gif    KZ.gif    MU.gif        PR.gif  TC.gif  WF.gif
AQ.gif    CD.gif    ET.gif    HN.gif    LA.gif    MV.gif        PS.gif  TD.gif  WS.gif
AR.gif    CF.gif    EU.gif    HR.gif    LB.gif    MW.gif        PT.gif  TG.gif  YE.gif
AS.gif    CG.gif    FI.gif    HT.gif    LC.gif    MX.gif        PW.gif  TH.gif  YT.gif
AT.gif    CH.gif    FJ.gif    HU.gif    LI.gif    MY.gif        PY.gif  TJ.gif  YU.gif
AU.gif    CI.gif    FK.gif    ID.gif    LK.gif    MZ.gif        QA.gif  TK.gif  ZA.gif
AW.gif    CK.gif    FM.gif    IE.gif    LR.gif    NA.gif        RE.gif  TM.gif  ZM.gif
AZ.gif    CL.gif    FO.gif    IL.gif    LS.gif    NC.gif        RO.gif  TN.gif  ZW.gif
BA.gif    CM.gif    FR.gif    IN.gif    LT.gif    NE.gif        RU.gif  TO.gif  ZZ.gif
BB.gif    CN.gif    GA.gif    IO.gif    LU.gif    NF.gif        RW.gif  TR.gif
BD.gif    CO.gif    GB.gif    IQ.gif    LV.gif    NG.gif        SA.gif  TT.gif
BE.gif    CR.gif    GD.gif    IR.gif    LY.gif    NI.gif        SB.gif  TV.gif
BF.gif    CS.gif    GE.gif    IS.gif    MA.gif    NL.gif        SC.gif  TW.gif
BG.gif    CU.gif    GF.gif    IT.gif    MC.gif    noflag.gif  SD.gif  TZ.gif
BH.gif    CV.gif    GH.gif    JM.gif    MD.gif    NO.gif        SE.gif  UA.gif
BI.gif    CY.gif    GI.gif    JO.gif    MG.gif    NP.gif        SG.gif  UG.gif

./trunk/Tools/web/browser/img:
down.gif             server_browser_cooldark_src.jpg  [www.gif](www.gif)
server_browser_cooldark.jpg  up.gif

./trunk/Tools/web/browser/ip_files:
0.php     12.php   15.php   18.php   219.php  249.php  48.php  78.php
100.php  130.php  160.php  190.php  21.php   24.php   49.php  79.php
101.php  131.php  161.php  191.php  220.php  250.php  4.php   7.php
102.php  132.php  162.php  192.php  221.php  251.php  50.php  80.php
103.php  133.php  163.php  193.php  222.php  252.php  51.php  81.php
104.php  134.php  164.php  194.php  223.php  253.php  52.php  82.php
105.php  135.php  165.php  195.php  224.php  254.php  53.php  83.php
106.php  136.php  166.php  196.php  225.php  255.php  54.php  84.php
107.php  137.php  167.php  197.php  226.php  25.php   55.php  85.php
108.php  138.php  168.php  198.php  227.php  26.php   56.php  86.php
109.php  139.php  169.php  199.php  228.php  27.php   57.php  87.php
10.php     13.php   16.php   19.php   229.php  28.php   58.php  88.php
110.php  140.php  170.php  1.php    22.php   29.php   59.php  89.php
111.php  141.php  171.php  200.php  230.php  2.php    5.php   8.php
112.php  142.php  172.php  201.php  231.php  30.php   60.php  90.php
113.php  143.php  173.php  202.php  232.php  31.php   61.php  91.php
114.php  144.php  174.php  203.php  233.php  32.php   62.php  92.php
115.php  145.php  175.php  204.php  234.php  33.php   63.php  93.php
116.php  146.php  176.php  205.php  235.php  34.php   64.php  94.php
117.php  147.php  177.php  206.php  236.php  35.php   65.php  95.php
118.php  148.php  178.php  207.php  237.php  36.php   66.php  96.php
119.php  149.php  179.php  208.php  238.php  37.php   67.php  97.php
11.php     14.php   17.php   209.php  239.php  38.php   68.php  98.php
120.php  150.php  180.php  20.php   23.php   39.php   69.php  99.php
121.php  151.php  181.php  210.php  240.php  3.php    6.php   9.php
122.php  152.php  182.php  211.php  241.php  40.php   70.php  countries.php
123.php  153.php  183.php  212.php  242.php  41.php   71.php  readme.txt
124.php  154.php  184.php  213.php  243.php  42.php   72.php  sources.txt
125.php  155.php  185.php  214.php  244.php  43.php   73.php  unknown.php
126.php  156.php  186.php  215.php  245.php  44.php   74.php
127.php  157.php  187.php  216.php  246.php  45.php   75.php
128.php  158.php  188.php  217.php  247.php  46.php   76.php
129.php  159.php  189.php  218.php  248.php  47.php   77.php

./trunk/Tools/web/browser/maps:
1st  3rd  default_341x256.jpg  default_80x60.jpg

./trunk/Tools/web/browser/maps/1st:
aoa-atlantis_341x256.jpg     dm-crucible2k8_341x256.jpg
aoa-atlantis_80x60.jpg         dm-crucible2k8_80x60.jpg
aoa-corrosion_341x256.jpg    dm-crucible_341x256.jpg
aoa-corrosion_80x60.jpg      dm-crucible_80x60.jpg
aoa-frost_341x256.jpg         dm-deimos2k9_341x256.jpg
aoa-frost_80x60.jpg         dm-deimos2k9_80x60.jpg
aoa-morpheus_341x256.jpg     dm-dismal2k8_341x256.jpg
aoa-morpheus_80x60.jpg         dm-dismal2k8_80x60.jpg
aoa-zorn_341x256.jpg         dm-dread_341x256.jpg
aoa-zorn_80x60.jpg         dm-dread_80x60.jpg
cp-grindery_341x256.jpg      dm-dynamo2k8_341x256.jpg
cp-grindery_80x60.jpg         dm-dynamo2k8_80x60.jpg
cp-ribeye_341x256.jpg         dm-eternal_341x256.jpg
cp-ribeye_80x60.jpg         dm-eternal_80x60.jpg
ctf-atlantis_341x256.jpg     dm-europa2k8_341x256.jpg
ctf-atlantis_80x60.jpg         dm-europa2k8_80x60.jpg
ctf-chromium_341x256.jpg     dm-furious2k8_341x256.jpg
ctf-chromium_80x60.jpg         dm-furious2k8_80x60.jpg
ctf-corrosion_341x256.jpg    dm-horus_341x256.jpg
ctf-corrosion_80x60.jpg      dm-horus_80x60.jpg
ctf-cryogenic_341x256.jpg    dm-leviathan2k8_341x256.jpg
ctf-cryogenic_80x60.jpg      dm-leviathan2k8_80x60.jpg
ctf-europa2k8_341x256.jpg    dm-liberation_341x256.jpg
ctf-europa2k8_80x60.jpg      dm-liberation_80x60.jpg
ctf-frost_341x256.jpg         dm-omega2k8_341x256.jpg
ctf-frost_80x60.jpg         dm-omega2k8_80x60.jpg
ctf-icarus2_341x256.jpg      dm-omega_341x256.jpg
ctf-icarus2_80x60.jpg         dm-omega_80x60.jpg
ctf-titan2k8_341x256.jpg     dm-saucer_341x256.jpg
ctf-titan2k8_80x60.jpg         dm-saucer_80x60.jpg
ctf-vesuvius_341x256.jpg     dm-titan2k8_341x256.jpg
ctf-vesuvius_80x60.jpg         dm-titan2k8_80x60.jpg
ctf-zorn_341x256.jpg         dm-turbo2k8_341x256.jpg
ctf-zorn_80x60.jpg         dm-turbo2k8_80x60.jpg
db-chromium_341x256.jpg      dm-vesuvius_341x256.jpg
db-chromium_80x60.jpg         dm-vesuvius_80x60.jpg
db-icarus_341x256.jpg         dm-violator_341x256.jpg
db-icarus_80x60.jpg         dm-violator_80x60.jpg
db-vesuvius_341x256.jpg      dm-warmachine_341x256.jpg
db-vesuvius_80x60.jpg         dm-warmachine_80x60.jpg
dm-aquous_341x256.jpg         dm-zion_341x256.jpg
dm-aquous_80x60.jpg         dm-zion_80x60.jpg
dm-atlantis2k8_341x256.jpg   dm-zorn_341x256.jpg
dm-atlantis2k8_80x60.jpg     dm-zorn_80x60.jpg
dm-babel_341x256.jpg         tca-corrosion_341x256.jpg
dm-babel_80x60.jpg         tca-corrosion_80x60.jpg
dm-beyond_341x256.jpg         tca-cryogenic_341x256.jpg
dm-beyond_80x60.jpg         tca-cryogenic_80x60.jpg
dm-bloodfactory_341x256.jpg  tca-europa2k8_341x256.jpg
dm-bloodfactory_80x60.jpg    tca-europa2k8_80x60.jpg
dm-chasmatic_341x256.jpg     tca-frost_341x256.jpg
dm-chasmatic_80x60.jpg         tca-frost_80x60.jpg
dm-command_341x256.jpg         tca-titan2k8_341x256.jpg
dm-command_80x60.jpg         tca-titan2k8_80x60.jpg
dm-corrosion_341x256.jpg     tca-zion_341x256.jpg
dm-corrosion_80x60.jpg         tca-zion_80x60.jpg

./trunk/Tools/web/browser/maps/3rd:
ahtcity-aoa_341x256.jpg        dm-dynamo2_341x256.jpg
ahtcity-aoa_80x60.jpg        dm-dynamo2_80x60.jpg
ahtcity-ctf_341x256.jpg        dm-dynamo_341x256.jpg
ahtcity-ctf_80x60.jpg        dm-dynamo_80x60.jpg
ahtcity-dm_341x256.jpg        dm-egyptian_341x256.jpg
ahtcity-dm_80x60.jpg        dm-egyptian_80x60.jpg
aoa1_341x256.jpg        dm-electro_341x256.jpg
aoa1_80x60.jpg            dm-electro_80x60.jpg
aoa2_341x256.jpg        dm-europa_341x256.jpg
aoa2_80x60.jpg            dm-europa_80x60.jpg
aoa-ahtcity_341x256.jpg        dm-fortofpillars_341x256.jpg
aoa-ahtcity_80x60.jpg        dm-fortofpillars_80x60.jpg
aoa-aztec_341x256.jpg        dm-frontier2_341x256.jpg
aoa-aztec_80x60.jpg        dm-frontier2_80x60.jpg
aoa-aztec-dark_341x256.jpg    dm-frontier_341x256.jpg
aoa-aztec-dark_80x60.jpg    dm-frontier_80x60.jpg
aoa-carnage_341x256.jpg        dm-furious_341x256.jpg
aoa-carnage_80x60.jpg        dm-furious_80x60.jpg
aoa-infinity_run_341x256.jpg    dm-gauntlet_341x256.jpg
aoa-infinity_run_80x60.jpg    dm-gauntlet_80x60.jpg
aoa-killbox_341x256.jpg        dm-grindery_341x256.jpg
aoa-killbox_80x60.jpg        dm-grindery_80x60.jpg
aoa-magma_341x256.jpg        dm-hungary_341x256.jpg
aoa-magma_80x60.jpg        dm-hungary_80x60.jpg
aoa-meatgrinder_341x256.jpg    dm-hypercube_341x256.jpg
aoa-meatgrinder_80x60.jpg    dm-hypercube_80x60.jpg
aoa-meatgrinder-x2_341x256.jpg    dm-inferno_341x256.jpg
aoa-meatgrinder-x2_80x60.jpg    dm-inferno_80x60.jpg
aoa-mgcity_341x256.jpg        dm-infinib_341x256.jpg
aoa-mgcity_80x60.jpg        dm-infinib_80x60.jpg
aoa-obsidian_341x256.jpg    dm-infinic_341x256.jpg
aoa-obsidian_80x60.jpg        dm-infinic_80x60.jpg
aoa-q3dm17_341x256.jpg        dm-infinity_341x256.jpg
aoa-q3dm17_80x60.jpg        dm-infinity_80x60.jpg
aoa-signs-day_341x256.jpg    dmintro_341x256.jpg
aoa-signs-day_80x60.jpg        dmintro_80x60.jpg
aoa-signs-fog_341x256.jpg    dm-khanate_341x256.jpg
aoa-signs-fog_80x60.jpg        dm-khanate_80x60.jpg
aoa-signs-night_341x256.jpg    dm-killbox_341x256.jpg
aoa-signs-night_80x60.jpg    dm-killbox_80x60.jpg
aoa-tourney0_341x256.jpg    dm-leviathan_341x256.jpg
aoa-tourney0_80x60.jpg        dm-leviathan_80x60.jpg
ctf0_341x256.jpg        dm-magma_341x256.jpg
ctf0_80x60.jpg            dm-magma_80x60.jpg
ctf1_341x256.jpg        dm-martianfactory_341x256.jpg
ctf1_80x60.jpg            dm-martianfactory_80x60.jpg
ctf2_341x256.jpg        dm-maya_341x256.jpg
ctf2_80x60.jpg            dm-maya_80x60.jpg
ctf-2fortx_341x256.jpg        dm-meatgrinder_341x256.jpg
ctf-2fortx_80x60.jpg        dm-meatgrinder_80x60.jpg
ctf3_341x256.jpg        dm-meatgrinder-x2_341x256.jpg
ctf3_80x60.jpg            dm-meatgrinder-x2_80x60.jpg
ctf-ahtcity_341x256.jpg        dm-merterprizon_341x256.jpg
ctf-ahtcity_80x60.jpg        dm-merterprizon_80x60.jpg
ctf-blood_341x256.jpg        dm-mgcity2-beta_341x256.jpg
ctf-blood_80x60.jpg        dm-mgcity2-beta_80x60.jpg
ctf-europa_341x256.jpg        dm-mgcity_341x256.jpg
ctf-europa_80x60.jpg        dm-mgcity_80x60.jpg
ctf-fortofpillars_341x256.jpg    dm-module_341x256.jpg
ctf-fortofpillars_80x60.jpg    dm-module_80x60.jpg
ctf-icarus_341x256.jpg        dm-mp1m10_341x256.jpg
ctf-icarus_80x60.jpg        dm-mp1m10_80x60.jpg
ctf-killbox_341x256.jpg        dm-negator_341x256.jpg
ctf-killbox_80x60.jpg        dm-negator_80x60.jpg
ctf-magma_341x256.jpg        dm-nkitrn1_341x256.jpg
ctf-magma_80x60.jpg        dm-nkitrn1_80x60.jpg
ctf-meatgrinder-x2_341x256.jpg    dm-obsidian2_341x256.jpg
ctf-meatgrinder-x2_80x60.jpg    dm-obsidian2_80x60.jpg
ctf-mgcity_341x256.jpg        dm-obsidian_341x256.jpg
ctf-mgcity_80x60.jpg        dm-obsidian_80x60.jpg
ctf-rockwar_341x256.jpg        dm-outpost_341x256.jpg
ctf-rockwar_80x60.jpg        dm-outpost_80x60.jpg
ctf-spacejam_341x256.jpg    dm-probe_341x256.jpg
ctf-spacejam_80x60.jpg        dm-probe_80x60.jpg
ctf-stronghold_341x256.jpg    dm-q1dm4_341x256.jpg
ctf-stronghold_80x60.jpg    dm-q1dm4_80x60.jpg
ctf-terminal_341x256.jpg    dm-q1dm6_341x256.jpg
ctf-terminal_80x60.jpg        dm-q1dm6_80x60.jpg
ctf-titan_341x256.jpg        dm-q3dm17_341x256.jpg
ctf-titan_80x60.jpg        dm-q3dm17_80x60.jpg
db-egyptian_341x256.jpg        dm-quakepanic_341x256.jpg
db-egyptian_80x60.jpg        dm-quakepanic_80x60.jpg
db-electro_341x256.jpg        dm-reactor4_341x256.jpg
db-electro_80x60.jpg        dm-reactor4_80x60.jpg
db-europa_341x256.jpg        dm-redred_341x256.jpg
db-europa_80x60.jpg        dm-redred_80x60.jpg
db-frontier_341x256.jpg        dm-rockasm_341x256.jpg
db-frontier_80x60.jpg        dm-rockasm_80x60.jpg
db-inferno_341x256.jpg        dm-signs-day_341x256.jpg
db-inferno_80x60.jpg        dm-signs-day_80x60.jpg
db-infinity_341x256.jpg        dm-signs-fog_341x256.jpg
db-infinity_80x60.jpg        dm-signs-fog_80x60.jpg
db-killbox_341x256.jpg        dm-signs-night_341x256.jpg
db-killbox_80x60.jpg        dm-signs-night_80x60.jpg
db-magma_341x256.jpg        dm-sin-khanate_341x256.jpg
db-magma_80x60.jpg        dm-sin-khanate_80x60.jpg
db-meatgrinder_341x256.jpg    dm-tangle_341x256.jpg
db-meatgrinder_80x60.jpg    dm-tangle_80x60.jpg
db-meatgrinder-x2_341x256.jpg    dm-titan_341x256.jpg
db-meatgrinder-x2_80x60.jpg    dm-titan_80x60.jpg
db-obsidian_341x256.jpg        dm-turbo_341x256.jpg
db-obsidian_80x60.jpg        dm-turbo_80x60.jpg
db-q3dm17_341x256.jpg        dm-ufc2-moth_341x256.jpg
db-q3dm17_80x60.jpg        dm-ufc2-moth_80x60.jpg
db-stronghold_341x256.jpg    dm-ufc_341x256.jpg
db-stronghold_80x60.jpg        dm-ufc_80x60.jpg
dm0_341x256.jpg            mgcity-aoa_341x256.jpg
dm0_80x60.jpg            mgcity-aoa_80x60.jpg
dm10_341x256.jpg        mgcity-ctf_341x256.jpg
dm10_80x60.jpg            mgcity-ctf_80x60.jpg
dm11_341x256.jpg        mgcity-dm_341x256.jpg
dm11_80x60.jpg            mgcity-dm_80x60.jpg
dm12a_341x256.jpg        q3dm18_341x256.jpg
dm12a_80x60.jpg            q3dm18_80x60.jpg
dm1_341x256.jpg            quakepanic01_341x256.jpg
dm1_80x60.jpg            quakepanic01_80x60.jpg
dm2_341x256.jpg            restplace_341x256.jpg
dm2_80x60.jpg            restplace_80x60.jpg
dm3_341x256.jpg            rockasm_341x256.jpg
dm3_80x60.jpg            rockasm_80x60.jpg
dm4_341x256.jpg            rockwar-ctf_341x256.jpg
dm4_80x60.jpg            rockwar-ctf_80x60.jpg
dm5_341x256.jpg            tca-europa_341x256.jpg
dm5_80x60.jpg            tca-europa_80x60.jpg
dm6_341x256.jpg            tca-europa-aoa_341x256.jpg
dm6_80x60.jpg            tca-europa-aoa_80x60.jpg
dm7_341x256.jpg            tca-killbox_341x256.jpg
dm7_80x60.jpg            tca-killbox_80x60.jpg
dm8_341x256.jpg            tca-killbox-aoa_341x256.jpg
dm8_80x60.jpg            tca-killbox-aoa_80x60.jpg
dm-ahtcity_341x256.jpg        tca-magma_341x256.jpg
dm-ahtcity_80x60.jpg        tca-magma_80x60.jpg
dm-area51_341x256.jpg        tca-meatgrinder-x2_341x256.jpg
dm-area51_80x60.jpg        tca-meatgrinder-x2_80x60.jpg
dm-atlantis_341x256.jpg        tca-meatgrinder-x2-a_341x256.jpg
dm-atlantis_80x60.jpg        tca-meatgrinder-x2-a_80x60.jpg
dm-aztec_341x256.jpg        tca-meatgrinder-x2-aoa_341x256.jpg
dm-aztec_80x60.jpg        tca-meatgrinder-x2-aoa_80x60.jpg
dm-aztec-dark_341x256.jpg    tca-module_341x256.jpg
dm-aztec-dark_80x60.jpg        tca-module_80x60.jpg
dm-aztec-matrix_341x256.jpg    tca-q3dm17_341x256.jpg
dm-aztec-matrix_80x60.jpg    tca-q3dm17_80x60.jpg
dm-blood_341x256.jpg        tca-q3dm17-aoa_341x256.jpg
dm-blood_80x60.jpg        tca-q3dm17-aoa_80x60.jpg
dm-bounce_341x256.jpg        tca-spacejam_341x256.jpg
dm-bounce_80x60.jpg        tca-spacejam_80x60.jpg
dm-catfight_341x256.jpg        tca-spacejam-aoa_341x256.jpg
dm-catfight_80x60.jpg        tca-spacejam-aoa_80x60.jpg
dm-cavern_341x256.jpg        tca-stronghold_341x256.jpg
dm-cavern_80x60.jpg        tca-stronghold_80x60.jpg
dm-chthon_341x256.jpg        tca-terminal-aoa_341x256.jpg
dm-chthon_80x60.jpg        tca-terminal-aoa_80x60.jpg
dm-deathbox_341x256.jpg        tca-titan_341x256.jpg
dm-deathbox_80x60.jpg        tca-titan_80x60.jpg
dm-deimos_341x256.jpg        tourney0_341x256.jpg
dm-deimos_80x60.jpg        tourney0_80x60.jpg
dm-dismal_341x256.jpg        tourney1_341x256.jpg
dm-dismal_80x60.jpg        tourney1_80x60.jpg
dm-dune_341x256.jpg        tourney2_341x256.jpg
dm-dune_80x60.jpg        tourney2_80x60.jpg
dm-dungeon_341x256.jpg        tourney3_341x256.jpg
dm-dungeon_80x60.jpg        tourney3_80x60.jpg

./trunk/Tools/web/live:
aabanner.jpg  config.php  COPYING  font  index.html  live.php

./trunk/Tools/web/live/font:
NEUROPOL.TTF  READ_ME.TXT

./trunk/Tools/web/rss:
rss.php

./trunk/Tools/web/scan:
index.html  scan.php

./trunk/Tools/WinInstall:
alienarena2007.iss

```

[/SIZE]

Code tags are your friend, lol.  Just highlight the area of text you want to tag and hit the # button at the top of the message window.  As for the compile problem sorry, Im too much of a newb to be any help there.

---

### Post by AxelMan0 on 2009-08-09
```
Oh I was wondering how to make those boxes haha thanks
``` 

:)

---

