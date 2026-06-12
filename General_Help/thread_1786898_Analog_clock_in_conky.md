---
title: "Analog clock in conky"
date: 2011-06-20
forum: General Help
---

### Post by Robert Finley on 2011-06-20
Can someone pls explain how or point me to some info on setting up an analog clock with conky?  I have done quite a bit of searching and I'm just not finding it.

I already have 2 conkys running, a hardware monitor in the upper-right and a RSS feed in the lower-left.  I'm just trying to get a basic white analog clock it the upper-left of my screen.

I'm running a pretty old machine and don't have the hardware resources to run something like cairo-clock.

---

### Post by Habitual on 2011-06-20
[Conky Mega-Thread](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

[Conky Pitstop](http://conky.pitstop.free.fr/wiki/index.php5?title=Main_Page)

---

### Post by VCoolio on 2011-06-20
Here are two examples for conky: [link]("http://ubuntuforums.org/showpost.php?p=7041442&postcount=6440") with right script one page further [here]("http://ubuntuforums.org/showpost.php?p=7041727&postcount=6444"). And [this]("http://blog.conky.be/2009/10/19/widgets-in-conky-it-can-be-done/") is more or less the same.

---

### Post by Robert Finley on 2011-06-21
Thanks for the input.  The second link is a page I was actually looking at yesterday.  My problem is that I am not a programmer and I don't really know how to make it work.

I downloaded the files from both links.  I don't know how to execute them.  This is my first foray into trying to run a script with conky.  I am still reading about it.

---

### Post by Robert Finley on 2011-06-21
I don't know what to do with the files obtained from the first link.  The second link is a page with some instruction but it tells me I need to download a shell script and a module.  I have the shell script open in front of me but the module gives me an error when I try to open it with archive manager.

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors

---

### Post by Frogs Hair on 2011-06-21
You may have a corrupt package . You could try and download it again , I would be a little cautious with that particular package unless you trust the source.

---

### Post by Robert Finley on 2011-06-21
I have tried several times already :(  As far as the being careful, I don't really care..  This computer is a toy I built from spare parts specificly for learning linux.  I don't fear demolishing it.

---

### Post by Habitual on 2011-06-21
you *could* just Alt+F2
```
xclock -g +0+0 -update 1
```

---

### Post by Habitual on 2011-06-21
```
# Static and Variable Values used by Habitual/John Jones

# Static Values
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_xft yes
draw_outline no
draw_borders no
uppercase no
draw_shades no
draw_shades yes
double_buffer yes
border_width 0
text_buffer_size 2048
default_color white
update_interval 1.0

# Variable Values # These values are the ONLY thing that change from widget to widget
alignment tl
gap_x 5
gap_y 44
minimum_size 10 1
maximum_width 20

TEXT
${execpi 600 xclock -g +0+0 -update 1}
```to run it, add it to your conky startup script.
Here's a portion of mine
```
conky -c /home/jj/Documents/Conky/Weather/forecast &
conky -c /home/jj/Documents/Conky/Calendar/horizontal_calendar &
conky -c /home/jj/Documents/Conky/Reminder/reminder &
```

---

### Post by Robert Finley on 2011-06-21
The xclock works, but it is not really what I'm trying to accomplish.  It is EXACTLY what I want, if the background were transparent and it wasn't windowed.  I think the air clock mentioned earlier, though a little flashier then I need, is still closer to what I want.  Still trying to figure out how to acquire the script.

---

### Post by Robert Finley on 2011-06-21
Ok, working off a script I found HERE:[http://londonali1010.deviantart.com/art/quot-Air-quot-Clock-for-Conky-141958642](http://londonali1010.deviantart.com/art/quot-Air-quot-Clock-for-Conky-141958642)

I don't understand how to execute it though. I saved the unpacked folder in my home folder.  It contains a .lua file and a .txt file.  I opened them both in gedit and the .lua file told me to add the following before TEXT:

 lua_load ~/scripts/clock.lua
 lua_draw_hook_pre draw_clock

So I made a .conkyclock file (by just editing the same basic script I'm using for my other 2 conkys) and added it to my start file.  Now my script looks like this:

own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
double_buffer yes
use_spacer yes
use_xft yes
update_interval 3.0
minimum_size 400 5
draw_shades yes
draw_outline no # amplifies text if yes
draw_borders no
uppercase no 
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
own_window_colour brown
own_window_transparent yes
alignment top_left
gap_x 10
gap_y 10
override_utf8_locale no
xftfont Terminus:size=10
xftalpha 0.8
lua_load home/robert/.conky/air_clock/clock.lua
lua_draw_hook_pre draw_clock
TEXT



Ok.. that's as far as I've gotten.  I don't know what goes after TEXT, I don't know what the .txt file I downloaded is for, and I do know it doesn't work yet.

---

### Post by Habitual on 2011-06-21
My reply was merely to let you know you had "options"...

Here's the original article by the original author of the Conky+LUA clock scripts. (**Freelance editors**: Don't shoot me if I am wrong about the "author" or "original")

[http://blog.conky.be/2009/09/28/lua-cairo-bindings-getting-started/](http://blog.conky.be/2009/09/28/lua-cairo-bindings-getting-started/)

and another link to a similar conky+LUA script by londonali1010

[http://londonali1010.deviantart.com/art/quot-Air-quot-Clock-for-Conky-141958642?q=sort%3Atime+favby%3Adevious-quark&qo=1](http://londonali1010.deviantart.com/art/quot-Air-quot-Clock-for-Conky-141958642?q=sort%3Atime+favby%3Adevious-quark&qo=1)

and the Conky Pitstop article on same "Air Clock"
[http://conky.pitstop.free.fr/wiki/index.php5?title=Conky_widgets_%28en%29](http://conky.pitstop.free.fr/wiki/index.php5?title=Conky_widgets_%28en%29)

google "Air Clock for Conky" for further leads on this subject.

---

### Post by Robert Finley on 2011-06-21
Hey wow! Thanks

---

### Post by Habitual on 2011-06-21
GMTA, I guess. :)

Nothing goes after TEXT. It's going to utilize the LUA bindings to draw a clock on the screen, not conky "TEXT" instructions.

---

### Post by Habitual on 2011-06-21
> **Robert Finley said:**
> ...lua_load home/robert/.conky/air_clock/clock.lua


**lua_load /path/to/clock.lua**

should call up the clock.

to verify: open a terminal and type:
```
find `pwd` -name clock.lua -type f
```

use that for the lua_load parameter.

Good Luck!

Conky Addicts Anonymous meetings are EVERY day at 12noon. :p

---

### Post by VCoolio on 2011-06-21
First download [conky_widgets.lua.tar](http://blog.conky.be/wp-content/uploads/2009/10/conky_widgets.lua.tar.gz) and [air_clock_wb.txt.tar.gz](http://blog.conky.be/wp-content/uploads/2009/10/air_clock_wb.txt.tar.gz).

Extract both, for example using unp which is awesome for extracting a lot of different archive types without bothering what flags you need:```

unp air_clock_wb.txt.tar.gz && unp conky_widgets.lua.tar.gz
```

Then open the lua file with your favorite editor and paste the contents of the txt file into it like explained in the lua file, so on line 23. Save the lua file.

Then create a conky config with all your favorite options and these lines just above TEXT:```
lua_load ~/scripts/conky_widgets.lua
lua_draw_hook_pre widgets
```
Modify the first line so it has the right path to where you saved your lua file.

A conky config like this one works```
# -- Conky settings -- #
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
own_window_type desktop #override
own_window_transparent yes
own_window_argb_visual yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

minimum_size 300 300
maximum_width 1000

alignment tl
gap_x 10
gap_y 10

# -- Lua Load -- #
lua_load ~/.conky/conkyclocktest/conky_widgets.lua
lua_draw_hook_pre widgets

TEXT
```

now run ```

conky -c /path/to/above/conkyrc
```

---

### Post by Robert Finley on 2011-06-21
> **VCoolio said:**
> 

# -- Lua Load -- #
lua_load ~/.conky/conkyclocktest/conky_widgets.lua


What does the ~ mean?

---

### Post by Robert Finley on 2011-06-21
> **VCoolio said:**
> ```

unp air_clock_wb.txt.tar.gz && unp conky_widgets.lua.tar.gz
```[/code]

Terminal (after installing unp):

robert@Desktop:~/Downloads$ unp air_clock_wb.txt.tar.gz && unp conky_widgets.lua.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
WARNING: There were errors while processing files!

:(

---

### Post by VCoolio on 2011-06-22
> **Robert Finley said:**
> What does the ~ mean?

~ is short for /home/<username>

The unp / tar error: sorry, works for me; don't know what to say. Maybe try xarchiver, it's a gui, may suit you more. But no biggy, I guess I'm allowed to post the contents here; if not an admin can remove if I'm slow on replies. This is the lua file with the txt file already pasted in.
```
--[[
Conky Widgets by londonali1010 (2009)

This script is meant to be a "shell" to hold a suite of widgets for use in Conky.

To configure:
+ Copy the widget's code block (will be framed by --(( WIDGET NAME )) and --(( END WIDGET NAME )), with "[" instead of "(") somewhere between "require 'cairo'" and "function conky_widgets()", ensuring not to paste into another widget's code block
+ To call the widget, add the following just before the last "end" of the entire script:
	cr = cairo_create(cs)
	NAME_OF_FUNCTION(cr, OPTIONS)
	cairo_destroy(cr)
+ Replace OPTIONS with the options for your widget (should be specified in the widget's code block) 

Call this script in Conky using the following before TEXT (assuming you save this script to ~/scripts/conky_widgets.lua):
	lua_load ~/scripts/conky_widgets.lua
	lua_draw_hook_pre widgets
	
Changelog:
+ v1.0 -- Original release (17.10.2009)
]]

require 'cairo'

--[[ AIR CLOCK WIDGET ]]
--[[ Options (xc, yc, size):
	"xc" and "yc" are the x and y coordinates of the centre of the clock, in pixels, relative to the top left of the Conky window
	"size" is the total size of the widget, in pixels ]]

function air_clock(cr, xc, yc, size)
	local offset = 0
	
	shadow_width = size * 0.03
	shadow_xoffset = 0
	shadow_yoffset = size * 0.01
	
	if shadow_xoffset >= shadow_yoffset then
		offset = shadow_xoffset
	else offset = shadow_yoffset
	end
	
	local clock_r = (size - 2 * offset) / (2 * 1.25)
		
	show_seconds=true
	
	-- Grab time
	
	local hours=os.date("%I")
	local mins=os.date("%M")
	local secs=os.date("%S")
	
	secs_arc=(2*math.pi/60)*secs
	mins_arc=(2*math.pi/60)*mins
	hours_arc=(2*math.pi/12)*hours+mins_arc/12
	
	-- Drop shadow
	
	local ds_pat=cairo_pattern_create_radial(xc+shadow_xoffset,yc+shadow_yoffset,clock_r*1.25,xc+shadow_xoffset,yc+shadow_yoffset,clock_r*1.25+shadow_width)
	cairo_pattern_add_color_stop_rgba(ds_pat,0,0,0,0,0.2)
	cairo_pattern_add_color_stop_rgba(ds_pat,1,0,0,0,0)
	
	cairo_move_to(cr,0,0)
	cairo_line_to(cr,conky_window.width,0)
	cairo_line_to(cr,conky_window.width, conky_window.height)
	cairo_line_to(cr,0,conky_window.height)
	cairo_close_path(cr)
	cairo_new_sub_path(cr)
	cairo_arc(cr,xc,yc,clock_r*1.25,0,2*math.pi)
	cairo_set_source(cr,ds_pat)
	cairo_set_fill_rule(cr,CAIRO_FILL_RULE_EVEN_ODD)
	cairo_fill(cr)
	
	-- Glassy border
	
	cairo_arc(cr,xc,yc,clock_r*1.25,0,2*math.pi)
	cairo_set_source_rgba(cr,0.5,0.5,0.5,0.2)
	cairo_set_line_width(cr,1)
	cairo_stroke(cr)
	
	local border_pat=cairo_pattern_create_linear(xc,yc-clock_r*1.25,xc,yc+clock_r*1.25)
	
	cairo_pattern_add_color_stop_rgba(border_pat,0,1,1,1,0.7)
	cairo_pattern_add_color_stop_rgba(border_pat,0.3,1,1,1,0)
	cairo_pattern_add_color_stop_rgba(border_pat,0.5,1,1,1,0)
	cairo_pattern_add_color_stop_rgba(border_pat,0.7,1,1,1,0)
	cairo_pattern_add_color_stop_rgba(border_pat,1,1,1,1,0.7)
	cairo_set_source(cr,border_pat)
	cairo_arc(cr,xc,yc,clock_r*1.125,0,2*math.pi)
	cairo_close_path(cr)
	cairo_set_line_width(cr,clock_r*0.25)
	cairo_stroke(cr)
	
	-- Set clock face
	
	cairo_arc(cr,xc,yc,clock_r,0,2*math.pi)
	cairo_close_path(cr)
	
	local face_pat=cairo_pattern_create_radial(xc,yc-clock_r*0.75,0,xc,yc,clock_r)
	
	cairo_pattern_add_color_stop_rgba(face_pat,0,1,1,1,0.9)
	cairo_pattern_add_color_stop_rgba(face_pat,0.5,1,1,1,0.9)
	cairo_pattern_add_color_stop_rgba(face_pat,1,0.9,0.9,0.9,0.9)
	cairo_set_source(cr,face_pat)
	cairo_fill_preserve(cr)
	cairo_set_source_rgba(cr,0.5,0.5,0.5,0.2)
	cairo_set_line_width(cr, 1)
	cairo_stroke (cr)
	
	-- Draw hour hand
	
	xh=xc+0.7*clock_r*math.sin(hours_arc)
	yh=yc-0.7*clock_r*math.cos(hours_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xh,yh)
	
	cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
	cairo_set_line_width(cr,5)
	cairo_set_source_rgba(cr,0,0,0,0.5)
	cairo_stroke(cr)
	
	-- Draw minute hand
	
	xm=xc+0.9*clock_r*math.sin(mins_arc)
	ym=yc-0.9*clock_r*math.cos(mins_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xm,ym)
	
	cairo_set_line_width(cr,3)
	cairo_stroke(cr)
	
	-- Draw seconds hand
	
	if show_seconds then
		xs=xc+0.9*clock_r*math.sin(secs_arc)
		ys=yc-0.9*clock_r*math.cos(secs_arc)
		cairo_move_to(cr,xc,yc)
		cairo_line_to(cr,xs,ys)
	
		cairo_set_line_width(cr,1)
		cairo_stroke(cr)
	end
end

--[[ END AIR CLOCK WIDGET ]]

--[[ RING WIDGET ]]
--[[ Options (name, arg, max, bg_colour, bg_alpha, xc, yc, radius, thickness, start_angle, end_angle):
	"name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
	"arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
	"max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
	"bg_colour" is the colour of the base ring.
	"bg_alpha" is the alpha value of the base ring.
	"fg_colour" is the colour of the indicator part of the ring.
	"fg_alpha" is the alpha value of the indicator part of the ring.
	"x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
	"radius" is the radius of the ring.
	"thickness" is the thickness of the ring, centred around the radius.
	"start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
	"end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle. ]]

function ring(cr, name, arg, max, bgc, bga, fgc, fga, xc, yc, r, t, sa, ea)
	local function rgb_to_r_g_b(colour,alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
	
	local function draw_ring(pct)
		local angle_0=sa*(2*math.pi/360)-math.pi/2
		local angle_f=ea*(2*math.pi/360)-math.pi/2
		local pct_arc=pct*(angle_f-angle_0)

		-- Draw background ring

		cairo_arc(cr,xc,yc,r,angle_0,angle_f)
		cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
		cairo_set_line_width(cr,t)
		cairo_stroke(cr)
	
		-- Draw indicator ring

		cairo_arc(cr,xc,yc,r,angle_0,angle_0+pct_arc)
		cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
		cairo_stroke(cr)
	end
	
	local function setup_ring()
		local str = ''
		local value = 0
		
		str = string.format('${%s %s}', name, arg)
		str = conky_parse(str)
		
		value = tonumber(str)
		if value == nil then value = 0 end
		pct = value/max
		
		draw_ring(pct)
	end	
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then setup_ring() end
end

--[[ END RING WIDGET ]]

function conky_widgets()
	if conky_window == nil then return end
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	
	cr = cairo_create(cs)
	air_clock(cr, 120, 120, 200) -- options: xc, yc, size
	cairo_destroy(cr)
	
	cr = cairo_create(cs)
	ring(cr, 'cpu', 'CPU0', 100, 0xFFFFFF, 0.2, 0xFFFFFF, 0.8, 920, 200, 50, 10, 0, 180) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
	cairo_destroy(cr)
	
	cr = cairo_create(cs)
	ring(cr, 'memperc', '', 100, 0xFFFFFF, 0.2, 0xFFFFFF, 0.8, 920, 300, 50, 10, 180, 360) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
	cairo_destroy(cr)	
	
	cr = cairo_create(cs)
	ring(cr, 'fs_used_perc', '/', 100, 0xFFFFFF, 0.2, 0xFFFFFF, 0.8, 920, 400, 50, 10, 0, 180) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
	cairo_destroy(cr)
	
	cr = cairo_create(cs)
	ring(cr, 'battery_percent', 'BAT1', 100, 0xFFFFFF, 0.2, 0xFFFFFF, 0.8, 920, 500, 50, 10, 180, 360) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
	cairo_destroy(cr)
end
```

---

### Post by Robert Finley on 2011-06-22
Ok thanks! That worked.  I now have a clock on my desktop.  It has a black box behind it though. I used the exact same code on the conky that calls the clock as I did on my other conkys.  It should be transparent. And it disappeared when I clicked on the desktop.

Screenshot: [http://i1129.photobucket.com/albums/m503/finley-rob/clock.png](http://i1129.photobucket.com/albums/m503/finley-rob/clock.png)

Do you have any idea what may cause this?

---

### Post by Robert Finley on 2011-06-22
Ok actually, I'm using the conky script posted earlier in this thread. I looks like this now:

# -- Conky settings -- #
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
own_window_type desktop #override
own_window_transparent yes
own_window_argb_visual yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

minimum_size 300 300
maximum_width 1000

alignment tl
gap_x 10
gap_y 10

# -- Lua Load -- #
lua_load ~/.conky/clock.lua
lua_draw_hook_pre widgets

TEXT

---

### Post by VCoolio on 2011-06-23
not sure if the black box issue is still there, but if it is, try messing with the "own_window_type desktop" line. It can have normal, override, dock and panel instead of desktop. Try in that order.

---

### Post by Robert Finley on 2011-06-23
The clock doesn't disappear when I click on the desktop anymore.  That only happens when "desktop" is the variable used.  I tried each of the variables listed though and none of them took care of the black box.  :(

---

### Post by VCoolio on 2011-06-23
Apparently the own_window_argb_visual yes part isn't working, or you don't have compositing enabled. Do you have the conky-all package installed? Try that. Any useful output when running conky -c /path/to/config in a terminal?

---

### Post by Robert Finley on 2011-06-23
I don't think I have  compositing enabled.  Do I need it?  Why are the other 2 conkys transparent?  How do I enable it?  I don't have any visual effects and I don't know how to enable them.  Compiz is installed but I don't see it anywhere.  In my Appearance settings I get Theme, Background, & Fonts, no visual effects tab. 

Can I just change the background color to match the color of my desktop?  I don't use a wallpaper.

---

### Post by Robert Finley on 2011-06-23
I went and read some on compositing.  I turned it on using the instructions here: 

[http://ubuntu-tutorials.com/2009/02/25/update-enable-compositing-the-easier-way/](http://ubuntu-tutorials.com/2009/02/25/update-enable-compositing-the-easier-way/)

That completely fixed the clock but it jacked up the other 2 conkys

screenshot: [http://i1129.photobucket.com/albums/m503/finley-rob/Screenshot-2.png](http://i1129.photobucket.com/albums/m503/finley-rob/Screenshot-2.png)


I feel like I'm getting warmer :)

---

### Post by Robert Finley on 2011-06-24
Well, I do have my analog clock now.  Thank you to everyone who have helped me. The rest is conky problems that I will figure out or start a new thread.

---

### Post by VCoolio on 2011-06-24
> **Robert Finley said:**
> [...]That completely fixed the clock but it jacked up the other 2 conkys

screenshot: [http://i1129.photobucket.com/albums/m503/finley-rob/Screenshot-2.png](http://i1129.photobucket.com/albums/m503/finley-rob/Screenshot-2.png)[...]

That's the drop shadows, it's a window manager thing, not conky. So open compiz config settings manager, window decorations section, shadow windows entry, enter
```
any & !(class = Conky)
```

---

### Post by Robert Finley on 2011-06-24
This is a screenshot of where I'm at: [http://i1129.photobucket.com/albums/m503/finley-rob/Screenshot-3.png](http://i1129.photobucket.com/albums/m503/finley-rob/Screenshot-3.png)

Everything is working! :)

I don't know what I did exactly to make it work.  The print is all very tiny now. 

Both scripts are more or less identical before TEXT.  This is what they look like:

# -- Conky settings -- #
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
own_window_type normal #override
own_window_transparent yes
own_window_argb_visual yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

minimum_size 300 300
maximum_width 1000

alignment bl
gap_x 10
gap_y 10

TEXT

${color 1793d1}NPR News:${color ffffff}
${rss [http://www.npr.org/rss/rss.php?id=1001](http://www.npr.org/rss/rss.php?id=1001) 10 item_titles 30 }


I have tried adding:

xftfont Terminus:size=12
xftalpha 0.8

It had no effect.  I am now trying to figure out how to increase the font size.  I like the way this desktop looks.  Thank your for your help getting the clock running.  The more I play with conky the more I love it :)

---

