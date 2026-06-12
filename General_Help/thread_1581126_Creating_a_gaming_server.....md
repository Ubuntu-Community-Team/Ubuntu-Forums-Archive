---
title: "Creating a gaming server...."
date: 2010-09-24
forum: General Help
---

### Post by Roxter.Rocking on 2010-09-24
Well, firstly Hi! I am new at this forum and I am getting this annoying problem with my gaming server. I am running a Garry's Mod server. Firstly I get a ton of errors, and secondly no one can connect to my server, it just says "Server is not responding.".
Here are the errors```

eugene@Agavi:~$ sudo  ./srcds_run -console -game garrysmod +maxplayers 16 +map gm_construct -autoupdate
sudo: ./srcds_run: command not found
eugene@Agavi:~$ cd orangebox
eugene@Agavi:~/orangebox$ sudo  ./srcds_run -console -game garrysmod +maxplayers 16 +map gm_construct -autoupdate
Auto detecting CPU
Using default binary: ./srcds_linux
Server will auto-restart if there is a crash.
INFO: Located steam: ../steam
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Base Source Shared Materials' version 8


Checking/Installing 'Base Source Shared Models' version 4


Checking/Installing 'Base Source Shared Sounds' version 4


Checking/Installing 'GarrysMod Content' version 101


Checking/Installing 'OB Linux Dedicated Server' version 65


HLDS installation up to date
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 102 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 0 multi object alertable sleeps
Using breakpad minidump system
Using breakpad crash handler

Console initialized.
ConVarRef mat_dxlevel doesn't point to an existing ConVar
Game.dll loaded for "Garry's Mod"
Setting breakpad minidump AppID = 4000
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Mounting hl2.. OK
Mounting cstrike.. Failed
Mounting dod.. Failed
Mounting ep2.. Failed
Mounting tf.. OK
Mounting episodic.. Failed
Mounting hl2mp.. Failed
Mounting portal.. OK
Mounting lostcoast.. Failed
Mounting hl1.. Failed
Mounting hl1mp.. Failed
Mounting zeno_clash.. OK
Garry's Mod server.dll Build #101 - Linux
[Sep 23 2010 12:14:30]
maxplayers set to 16
Unknown command "sv_allow_wait_command"
Unknown command "cl_cmdrate"
Unknown command "cl_updaterate"
Unknown command "rate"
maxplayers set to 16
Network: IP 127.0.1.1, mode MP, dedicated Yes, ports 27015 SV / 27005 CL
Lua initialized (Lua 5.1)
Registering gamemode 'sandbox' derived from 'base'
ScriptEnforce is disabled
Compressing lua files into data pack..
Skipped. Datapack exists.
ConVarRef room_type doesn't point to an existing ConVar
Executing dedicated server config file
Couldn't find scene 'scenes/player/heavy/low/specialcompleted11.vcd'
Couldn't find scene 'scenes/player/heavy/low/laughShort03.vcd'
Couldn't find scene 'scenes/player/heavy/low/specialcompleted07.vcd'
Couldn't find scene 'scenes/player/spy/low/taunt02.vcd'
Couldn't find scene 'scenes/Player/Scout/low/2540.vcd'
Couldn't find scene 'scenes/Player/Scout/low/2539.vcd'
Couldn't find scene 'scenes/Player/Scout/low/2550.vcd'
Couldn't find scene 'scenes/Player/Scout/low/2553.vcd'
Couldn't find scene 'scenes/Player/Scout/low/2552.vcd'
Couldn't find scene 'scenes/Player/Medic/low/1596.vcd'
[S_API FAIL] SteamAPI_Init() failed; unable to update local steamclient.dll. Continuing with current version anyway.
Installing breakpad exception handler for appid(srcds_linux)/version(1.0)
baseuser.cpp (431) : Assertion Failed: couldn't find entrypoint 'GetBaseUserDir'
/home/VALVE/rackadmin/buildslave/steam_rel_client_linux/build/src/clientdll/baseuser.cpp 431 Assertion Failed: couldn't find entrypoint 'GetBaseUserDir'
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Cannot change maxplayers while the server is running
Unknown command "sbox_allownpcs"
Unknown command "sbox_playergod"
Installing breakpad exception handler for appid(srcds_linux)/version(1.0)
Connection to Steam servers successful.
   VAC secure mode is activated.

```
I personally think people can't connect because of the ports, but I portforwarded and even tried enabling DMZ but nothing could help, I am sure the ports are open, and I have used commands on ubuntu to open them aswell. But still nothing, could anyone give me a response telling me specifics on the PF'ing or TV me for overall any errors I am getting?
ALSO I am running ubuntu SERVER edition....

---

### Post by Roxter.Rocking on 2010-09-24
I'm sorry I have to bump this thread so soon, but there are simply too many people posting new topics, and this one is already hitting the bottom of the list, and I don't know where to ask how to fix these problems.

---

### Post by Roxter.Rocking on 2010-09-24
are you going to force me to quadruple bump?

---

### Post by Siph0n on 2010-09-24
I believe you are ONLY suppose to bump after 24 hours... so STOP bumping. You will start to annoy people, and they will just ignore your thread.

---

### Post by Roxter.Rocking on 2010-09-24
whatever, screw this **** anyways, not like anyone knows anything about freaking portforwarding anyways...

---

### Post by Chesamo on 2010-10-01
Okay, I was three seconds away from responding when you posted that last comment. It was unneeded and deliberately inflammatory. Don't be impatient and people will respond eventually. Siph0n is right, bumping is only allowed for topics older than 24 hours. Christ.

I had the same problem as you when I set up a TF2 server. You have to start the server with the ```
-ip <local IP>
``` flag to allow non-local connections (eg. connections from computers other than the server). You can get the local IP by running ```
ifconfig |grep 'inet addr' | grep 192 |cut -f 2 -d ':' |cut -f 1 -d ' '
```

---

