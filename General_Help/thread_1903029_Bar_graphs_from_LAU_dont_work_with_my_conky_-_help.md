---
title: "Bar graphs from LAU dont work with my conky - help"
date: 2012-01-01
forum: General Help
---

### Post by geekyhawkes on 2012-01-01
I know there are lots of conky threads, and I have read / searched / googled as many as possible to try and work out what ive missed but im coming up blank.  

Im running the VIN conkyrc in Xubuntu 11.10 (64) and everything is working except the bargraphs.  Strangely the call of draw_bg.lua is working fine (as i tried # it out and the conky window changed as you would expect).

Here is the section from the conkyrc:

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/Conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/Conky/bargraph.lua
lua_draw_hook_post main_bars

Both draw_bg.lua and bargraph.lua are in the same folder, so a call for one you would think would work with the other?

Below is the contents of the bargraph.lua:

require 'cairo'

----------------START OF PARAMETERS ----------
function conky_main_bars()
	local bars_settings={
		{	--[ Graph for CPU1 ]--
			name="cpu",
			arg="cpu1",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=78,y=156,
			blocks=56,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU2 ]--
			name="cpu",
			arg="cpu2",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=78,y=170,
			blocks=56,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for Memory ]--
			name="memperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=220,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for Root ]--
                        name="fs_used_perc",
			arg="/",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=267,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
		{	--[ Graph for NAS ]--
			name="fs_used_perc",
			arg="/media/nas",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=295,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
	        {	--[ Graph for Swap ]--
                        name="swapperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=323,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		 }	
-----------END OF PARAMETERS--------------


    
	if conky_window == nil then return end
	
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	
	cr = cairo_create(cs)    
	--prevent segmentation error when reading cpu state
    if tonumber(conky_parse('${updates}'))>3 then
        for i in pairs(bars_settings) do
        	
        	draw_multi_bar_graph(bars_settings[i])
        	
        end
    end
	cairo_destroy(cr)
	cairo_surface_destroy(cs)
	cr=nil

end



function draw_multi_bar_graph(t)
	cairo_save(cr)
	--check values
	if t.draw_me == true then t.draw_me = nil end
	if t.draw_me ~= nil and conky_parse(tostring(t.draw_me)) ~= "1" then return end	
	if t.name==nil and t.argDarkOrange`/usr/bin/banshee --query-title --no-present | cut -f1- -d ${if_empty ${wireless_essid wlan0}}${else}1$endif==nil then 
		print ("No input values ... use parameters 'name' with 'arg' or only parameter 'arg' ") 
		return
	end
	if t.max==nil then
		print ("No maximum value defined, use 'max'")
		return
	end
	if t.name==nil then t.name="" end
	if t.arg==nil then t.arg="" end

	--set default values	
	if t.x == nil		then t.x = conky_window.width/2 end
	if t.y == nil		then t.y = conky_window.height/2 end
	if t.blocks == nil	then t.blocks=10 end
	if t.height == nil	then t.height=10 end
	if t.angle == nil 	then t.angle=0 end
	t.angle = t.angle*math.pi/180
	--line cap style
	if t.cap==nil		then t.cap = "b" end
	local cap="b"
	for i,v in ipairs({"s","r","b"}) do 
		if v==t.cap then cap=v end
	end
	local delta=0
	if t.cap=="r" or t.cap=="s" then delta = t.height end
	if cap=="s" then 	cap = CAIRO_LINE_CAP_SQUARE
	elseif cap=="r" then
		cap = CAIRO_LINE_CAP_ROUND
	elseif cap=="b" then
		cap = CAIRO_LINE_CAP_BUTT
	end
	--end line cap style
	--if t.led_effect == nil	then t.led_effect="r" end
	if t.width == nil	then t.width=20 end
	if t.space == nil	then t.space=2 end
	if t.radius == nil	then t.radius=0 end
	if t.angle_bar == nil	then t.angle_bar=0 end
	t.angle_bar = t.angle_bar*math.pi/360 --halt angle
	
	--colours
	if t.bg_colour == nil 	then t.bg_colour = {0x00FF00,0.5} end
	if #t.bg_colour~=2 		then t.bg_colour = {0x00FF00,0.5} end
	if t.fg_colour == nil 	then t.fg_colour = {0x00FF00,1} end
	if #t.fg_colour~=2 		then t.fg_colour = {0x00FF00,1} end
	if t.alarm_colour == nil 	then t.alarm_colour = t.fg_colour end
	if #t.alarm_colour~=2 		then t.alarm_colour = t.fg_colour end

	if t.mid_colour ~= nil then	
		for i=1, #t.mid_colour do    
		    if #t.mid_colour[i]~=3 then 
		    	print ("error in mid_color table")
		    	t.mid_colour[i]={1,0xFFFFFF,1} 
		    end
		end
    end
    
	if t.bg_led ~= nil and #t.bg_led~=2	then t.bg_led = t.bg_colour end
	if t.fg_led ~= nil and #t.fg_led~=2	then t.fg_led = t.fg_colour end
	if t.alarm_led~= nil and #t.alarm_led~=2 then t.alarm_led = t.fg_led end
	
	if t.led_effect~=nil then
		if t.bg_led == nil then t.bg_led = t.bg_colour end
		if t.fg_led == nil 	then t.fg_led = t.fg_colour end
		if t.alarm_led == nil  then t.alarm_led = t.fg_led end
	end
	

	if t.alarm==nil then t.alarm = t.max end --0.8*t.max end
	if t.smooth == nil then t.smooth = false end

	if t.skew_x == nil then 
		t.skew_x=0 
	else
		t.skew_x = math.pi*t.skew_x/180	
	end
	if t.skew_y == nil then 
		t.skew_y=0
	else
		t.skew_y = math.pi*t.skew_y/180	
	end
	
	if t.reflection_alpha==nil then t.reflection_alpha=0 end
	if t.reflection_length==nil then t.reflection_length=1 end
	if t.reflection_scale==nil then t.reflection_scale=1 end
	
	--end of default values
	

 	local function rgb_to_r_g_b(col_a)
		return ((col_a[1] / 0x10000) % 0x100) / 255., ((_surface_destroy(cs)
	cairo_destroy(cr)
	end

Fairly standard as I can see yet i dont get any of the graphs in any of the sections. 

Hope someone can help, i have obviously missed something, just not sure what?

Thanks

---

### Post by geekyhawkes on 2012-01-03
Sorry to bump, but can anyone give me a steer on this?  Im a bit out of ideas myself..

---

### Post by stinkeye on 2012-01-04
Hi geekyhawkes,
I just came accross a similar problem with the vindsl conky.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11583304&postcount=19023")


Go back to the [**_[COLOR="darkred"]origin of the script[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10880292&postcount=4") 
and recopy the **bargraph_small.lua** script as it has been fixed.

P.S. When pasting code it makes your post easier to read if you use the "#" symbol
and post between the code blocks ...eg(CODE)[COLOR="Blue"]your code[/COLOR](/CODE)

---

### Post by geekyhawkes on 2012-01-05
Genius! All working now, glad it wasnt just me, and thanks for the CODE tip!

---

