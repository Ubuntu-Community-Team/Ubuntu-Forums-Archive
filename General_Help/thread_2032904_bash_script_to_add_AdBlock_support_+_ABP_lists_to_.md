---
title: "bash script to add AdBlock support + ABP lists to LuaKit"
date: 2012-07-24
forum: General Help
---

### Post by HiImTye on 2012-07-24
I just wrote a bash script to download, enable (or update) the [AdBlock]("https://github.com/mason-larobina/luakit/wiki/AdBlock-Lua-module") module for LuaKit and also to download (or update) any AdBlock Plus lists you specify. I have included a bunch of the EasyList lists in the 'lists' file. just run the bash script and it will do everything for you. make sure you specify a 'basefolder' in the bash script (I keep my bash scripts in '$HOME/Launchers' so that's what it's set to)
you will need to enable each AdBlock Plus list in LuaKit if you want to use them (as the AdBlock module defaults them to off).

make sure to put the '-AdBlockList' file in your 'basefolder' or change its' location within the script. the list is tab separated for easy editing.

edit: apparently the forums convert tabs to spaces, so I'll add the files as an attachment instead. just extract them to $HOME/Launchers (or else 'wherever you want' and edit the file accordingly)
edit: more cohearent explanation of how to get it working

---

