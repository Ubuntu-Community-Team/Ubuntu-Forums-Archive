---
title: "Conky Lua &amp; Wifi Questions"
date: 2011-12-22
forum: General Help
---

### Post by jmadero on 2011-12-22
Hi All,

Two separate problems, just decided to combine.

1st:

Whenever I try using conky + lua and need to use the 'max' function I am running into this error:

Conky: llua_do_call: function conky_main_bars execution failed: /home/joel/.conky/bargraph.lua:385: attempt to perform arithmetic on field 'max' (a string value)


Here is the code for the section of the lua script:

```

	local bars_settings={

		{
			name="fs_used",
			arg="/",
			max=conky_parse("${to_bytes ${fs_size /}}"),
			--alarm=1,--no alarm with 1 smooth block, don't do extra work here
			bg_colour={0x00ff00,0.25},
			fg_colour={0x00ff00,1},
			alarm_colour={0xff0000,1},
			x=5,y=112,
			angle=90,
			blocks=1,
			height=210,width=18,
			smooth=true,
			mid_colour={{0.5,0xffff00,1}},
		},

```


2nd: 

Is there a way for me to use the wifi strength object in conky without having to use sudo command to run the conky file. Right now if I run it as my regular user I get "UNK" for signal strength, if I run it as sudoer I get the strength just fine.


Thanks in advance

---

### Post by Habitual on 2011-12-22
[http://ubuntuforums.org/showthread.php?t=1280453&page=28]("http://ubuntuforums.org/showthread.php?t=1280453&page=28&nojs=1#goto_threadsearch")

---

