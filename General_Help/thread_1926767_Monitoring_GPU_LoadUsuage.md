---
title: "Monitoring *GPU* Load/Usuage?"
date: 2012-02-16
forum: General Help
---

### Post by jerm1027 on 2012-02-16
Hello all. I've searched the forums for a bit about this question and found several dead threads without anything to useful for this.

Basically, I want to know if there is a program that monitors **GPU**/gfx usage on Ubuntu/Linux. I'm currently using GKrellM to monitor system resources, but I haven't found anything to monitor the GPU usage. i also couldn't find anything with the default System Monitor either.

On Windows, I know there is a host of programs to do this, but I prefer [Process Hacker]("http://processhacker.sourceforge.net/") 2, which is essentially an Open-sourced version of Process Explorer. I'm looking for something similar on Ubuntu. See screen:
[http://processhacker.sourceforge.net/images/screenshots/sysinfo_large.png](http://processhacker.sourceforge.net/images/screenshots/sysinfo_large.png)

BTW - if there isn't a generic/all-purpose option, I would prefer something compatible with AMD GPU's, as I'm running the AMD Fusion C-60 APU equipped with a Radeon 6290.
Also, I'm using the Catalyst Control Center 12.1 with driver package 8.93

---

### Post by jerm1027 on 2012-04-02
Anyone have any suggestions? I'm still very much interested in monitoring my GPU usage and I haven't found anything yet.

---

### Post by zeljkojagust on 2012-04-02
Try lm-sensors, it requires a bit of editing and configuration, but there is enough info on the web.

---

### Post by jerm1027 on 2012-04-02
> **zeljkojagust said:**
> Try lm-sensors, it requires a bit of editing and configuration, but there is enough info on the web.

I was unaware lm-sensors was able to monitor load/usage. Every time I've set it up before, it would only monitor temps/voltage of CPU and chipset. After looking into the site, it appears that the GPU temp/load monitoring only works for nvidia gpus. All my systems run AMD/ATi GPU's, 

> 

[LIST]
[*]LM-Sensors and GPU temperatures (lmsens.rrd)
[LIST]
[*]Up to 16 temperature sensors supported for cores.
[*]Up to 2 temperature sensors supported for the motherboard.
[*]Up to 4 temperature sensors supported for the CPU.
[*]Up to 9 fan speeds supported.
[*]Up to 12 voltages supported.
[*]Up to 9 temperature sensors for GPU (nvidia).
[/LIST]
     
[*]NVIDIA temperatures and usage (nvidia.rrd)
[LIST]
[*]Up to 9 cards supported.
[*]Temperatures, GPU usage and memory usage (CUDA).
[/LIST]
 
[/LIST]
[http://www.monitorix.org/features.html](http://www.monitorix.org/features.html)


Is there something I'm missing?

If not, other suggestions? :confused:

---

### Post by zeljkojagust on 2012-04-02
> After looking into the site, it appears that the GPU temp/load monitoring only works for nvidia gpus.

Sorry, forget to mention that little detail...

---

### Post by HiImTye on 2012-04-03
whatever AMD software you use to manage your video card should have some sort of output commands

nVidia uses nvidia-settings, for instance, here is how I get conky to monitor my GPU temperature:
```
${color2}GPU:${color3} ${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | grep -o '[0-9]\{2,3\}'}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C
```

I'm sure that whatever software AMD uses (catalyst, if I'm not mistaken) has an equivalent

---

### Post by jerm1027 on 2012-04-04
> **HiImTye said:**
> whatever AMD software you use to manage your video card should have some sort of output commands

nVidia uses nvidia-settings, for instance, here is how I get conky to monitor my GPU temperature:
```
${color2}GPU:${color3} ${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | grep -o '[0-9]\{2,3\}'}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C
```I'm sure that whatever software AMD uses (catalyst, if I'm not mistaken) has an equivalent

I know I did run into a command that did display a static usage and temp report, but that isn't quite what I'm looking for. I would like something that actively refreshes. I actually forgot the command... might have been atitweak --status. I would definitely prefer something that would display a meter of some sort, like a plugin for GKrellM, or an applet, but even something similar to top for the gpu would be cool.

---

### Post by jerm1027 on 2012-04-05
So, with further searching, I cam across [this thread.]("http://ubuntuforums.org/showthread.php?t=1566126") Here is an actual command that works. This will display just the GPU load. 
```
aticonfig --adapter=0 --od-getclocks | grep -i GPU
```Now... I wonder if I integrate this command into GKrellM somehow... Time for exploration! :D

I'm still on the look-out for a program/plugin/applet that does this that is also compatible for ATi/AMD GPU's, so if anyone has knowledge on this, please share.

---

### Post by QIII on 2012-04-05
I don't remember that you can do that in gkrellm.

But you can create a conky and put something like this in conkyrc:

```
${voffset 0}${goto 35}${color white}${font Monaco:size=7}Load${goto 105}Temp${alignr 30}Fan speed
${voffset 0}${goto 47}${color white}${font Monaco:size=7}${execi 1 aticonfig --odgc --odgt --adapter=0 | egrep -i "load|temperature" | xargs echo | awk '{print $4 "   " $9 "°C "}'}${alignr 28}${execi 1 aticonfig --pplib-cmd "get fanspeed 0" | grep -i result | awk '{print $4}'} 
```Your exact code will vary from mine.

What I think you have above, by the way, is not load but the clock settings -- which are fixed.

---

### Post by jerm1027 on 2012-04-06
> **QIII said:**
> I don't remember that you can do that in gkrellm.

But you can create a conky and put something like this in conkyrc:

```
${voffset 0}${goto 35}${color white}${font Monaco:size=7}Load${goto 105}Temp${alignr 30}Fan speed
${voffset 0}${goto 47}${color white}${font Monaco:size=7}${execi 1 aticonfig --odgc --odgt --adapter=0 | egrep -i "load|temperature" | xargs echo | awk '{print $4 "   " $9 "°C "}'}${alignr 28}${execi 1 aticonfig --pplib-cmd "get fanspeed 0" | grep -i result | awk '{print $4}'} 
```Your exact code will vary from mine.

What I think you have above, by the way, is not load but the clock settings -- which are fixed.

I haven't tried conky. I'll give it a try and adjust the command accordingly. As for the command I listed earlier
```

jeremy@jeremy-AO722:~$ aticonfig --adapter=0 --od-getclocks | grep -i GPU
                 GPU load :    13%
jeremy@jeremy-AO722:~$ aticonfig --adapter=0 --od-getclocks | grep -i GPU
                 GPU load :    0%
jeremy@jeremy-AO722:~$ 

```

---

### Post by jack_hmr on 2012-04-08
I use conky and lua to get graphs for GPU load and temp.
Snippets below. Let me know if you want the entire scripts.

In conky_lunatico.lua
```
{
    name="exec aticonfig --adapter=0 --od-gettemperature | grep Temperature | awk '{print $5}'",           arg='',    max_value=100,
    x=420,                          y=625,
    graph_radius=86,
    graph_thickness=15,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.0,
    hand_fg_colour=0xEF5A29,       hand_fg_alpha=1.0,
    txt_radius=52,
    txt_weight=0,                  txt_size=13.0,
    txt_fg_colour=0xEF5A29,        txt_fg_alpha=1.0,
    graduation_radius=23,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='temp',
    caption_weight=1,              caption_size=12.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.5,
},
{
    name="exec aticonfig --adapter=0 --od-getclocks | grep GPU | awk '{print $4}' | rev | cut --characters 2- | rev",           arg='',    max_value=100,
    x=420,                          y=625,
    graph_radius=104,
    graph_thickness=15,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.1,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.0,
    hand_fg_colour=0xEF5A29,       hand_fg_alpha=1.0,
    txt_radius=125,
    txt_weight=0,                  txt_size=13.0,
    txt_fg_colour=0xEF5A29,        txt_fg_alpha=1.0,
    graduation_radius=23,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='load',
    caption_weight=1,              caption_size=12.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.5,
},
}


-------------------------------------------------------------------------------
--
-- Grab info and give it back to conky for use in lua_graph
--
-- returns the gpu load
function conky_gpu_load()
	return tonumber(conky_parse("${exec aticonfig --adapter=0 --od-getclocks | grep GPU | awk '{print $4}' | rev | cut --characters 2- | rev}"))
end

-- returns the gpu temp
function conky_gpu_temp()
	return tonumber(conky_parse("${exec aticonfig --adapter=0 --od-gettemperature | grep Temperature | awk '{print $5}'}"))
end
```

In .conkyrc:
```
${voffset 145}
${offset 400}${font Ubuntu:size=12,weight:bold}${color}GPU
${offset 431}${font Ubuntu:size=10,weight:bold}${color}Temp${voffset -20}${lua_graph conky_gpu_temp 30,117 00FFFF FF0000 90 -t}
${offset 436}${font Ubuntu:size=10,weight:bold}${color}Load${voffset -20}${lua_graph conky_gpu_load 30,117 888888 EF5A29 100 -t}
```

---

