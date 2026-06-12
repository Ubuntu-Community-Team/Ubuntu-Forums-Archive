---
title: "Conky and new line"
date: 2010-06-21
forum: General Help
---

### Post by rajmahendra on 2010-06-21
I am using Ubuntu 10.4 and Conky new version.

I downloaded some conkyrc files from net and trying to test for all the output of Conky on my desktop, on my screen end of each line i see a inverted rectangle! i think its due to newline!

can someone help me how to remove this ?

---

### Post by WorMzy on 2010-06-21
Could you post one of them here? Embed it within CODE tags. I have multiple lines in my conkyrc, and it doesn't display any squares.

---

### Post by rajmahendra on 2010-06-21
```

# torsmo configuration

# set to yes if you want tormo to be forked in the background
background no

# X font used, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
font 8x13
#font 9x15
# font *mintsmild.se*
# font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Minimum size of text area
minimum_size 330 10

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 2

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color green
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 25
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  temp1                             Temperature #1 from i2c-sensors, same as 
#                                    ${i2c temp 1}                            
#  temp2                             Temperature #2 from i2c-sensors, same as 
#                                    ${i2c temp 2}                            
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen


TEXT
$nodename - $sysname $kernel on $machine
${color lightgrey}$stippled_hr
${color #0077ff}Date: $color ${time %A,  %d,  %B}
${color #0077ff}Time: $color ${time %k:%M:%S} ${color #0077ff}Uptime: $color $uptime
${color lightgrey}$stippled_hr
${color #0077ff}CPU Usage:$color ${cpu}% ${color #0077ff}Procs:$color $processes ${color #0077ff}Running:$color $running_processes ${color #0077ff}
${color #0077ff}${cpubar}
${color #0077ff}RAM Usage: $color $mem/$memmax - $memperc% ${color #0077ff}$membar
${color #0077ff}Swap Usage:$color $swap/$swapmax - $swapperc% ${color #0077ff}${swapbar}
${color #0077ff}Networking:
 Up:$color ${upspeed} k/s${color #0077ff} - Down:$color ${downspeed} k/s
${color #0077ff}File systems:             
 ${color #0077ff}/         $color${fs_used /}/${fs_size /}${color #0077ff} ${fs_bar /}
 ${color #0077ff}/opt      $color${fs_used /opt}/${fs_size /opt}${color #0077ff} ${fs_bar /opt}
${color #0077ff}Top Processes:
${color #0077ff}${exec /alex/torsmo-0.17/ps} 

```

---

### Post by rajmahendra on 2010-06-21
one more 

```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
# fiddle with window
use_spacer yes
use_xft yes
# Update interval in seconds
update_interval 3.0
# Minimum size of text area
minimum_size 400 5
# Draw shades?
draw_shades yes
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
# Stippled borders?
stippled_borders 8

# border margins
border_margin 4
# border width
border_width 1
# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white
own_window_colour brown
own_window_transparent yes
# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
# Gap between borders of screen and text
gap_x 10
gap_y 10
# stuff after 'TEXT' will be formatted on screen
override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8
TEXT
${offset 0}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 0}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 0}${color slate grey}UpTime: ${color }$uptime
${offset 0}${color slate grey}Kern:${color }$kernel
${offset 0}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 0}${cpugraph 20,130 000000 ffffff}
${offset 0}${color slate grey}Load: ${color }$loadavg
${offset 0}${color slate grey}Processes: ${color }$processes
${offset 0}${color slate grey}Running:   ${color }$running_processes
${offset 0}${color slate grey}Highest CPU:
${offset 0}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 0}${color lightgrey} ${top name 2}${top cpu 2}
${offset 0}${color lightgrey} ${top name 3}${top cpu 3}
${offset 0}${color lightgrey} ${top name 4}${top cpu 4}
${offset 0}${color slate grey}Highest MEM:
${offset 0}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 0}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 0}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 0}${color lightgrey} ${top_mem name 4}${top_mem mem 4}
${offset 0}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 0}${membar 3,100}
${offset 0}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 0}${swapbar 3,100}
${offset 0}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 0}${fs_bar 3,100 /}
${offset 0}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 0}${fs_bar 3,100 /home}
${offset 0}${color slate grey}NET:
${offset 0}${color}Up: ${color }${upspeed eth0} k/s
${offset 0}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 0}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 0}${downspeedgraph eth0 20,130 000000 ffffff}

```

---

### Post by WorMzy on 2010-06-21
Both of those work fine for me, although in the second example "use_spacer" should have the value of "right", "left", or "none", and the "border_margin" variable doesn't seem to have any use in the version of conky I'm using.

In any case, neither displays the rectangles you described, so I'm assuming that the problem lies somewhere else. How did you install conky?

---

### Post by stinkeye on 2010-06-21
> **WorMzy said:**
> Both of those work fine for me

Same here. Possibly try to copy and paste your code again from your forum post. Could be that the original was created with windows.
I'm using the **conky-all** package, available in synaptic.

---

### Post by rajmahendra on 2010-06-21
i am trying to talk screen shot but its also not working :( print screen!

---

### Post by rajmahendra on 2010-06-21
my Conky output... its still showing the inverted rectangle at the end of each line.

---

### Post by rajmahendra on 2010-06-22
anyone know what the problem in this ?

---

### Post by 4Orbs on 2010-06-22
I used your conkyrc (the second one you posted) on my computer and those little squares don't show up. But when I started conky with the terminal, I got this message
> Use Spacer should have an argument of left, right or none
Your line of Use Spacer has an argument of "yes" but I don't know if that's what causes the little rectangles (as I said, they don't appear for me). Also, check out the third screenshot below.

---

### Post by rajmahendra on 2010-07-21
how can i run Conky automatically? It may be due to running using command prompt.

---

### Post by stinkeye on 2010-07-21
> **rajmahendra said:**
> how can i run Conky automatically? It may be due to running using command prompt.
I dont think that would be causing your problem.

Run the default conky config and see if you still get boxes.
```
conky -c /etc/conky/conky.conf
```

Should look similar to attached pic.



You can also try other configs using the same command. The "**-c**" tells conky to load a particular config.
```
conky -c [COLOR="Purple"]/path/to_your/conky_config[/COLOR]
```

[**_[COLOR="DarkRed"]Thread for conky configs[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by sylvainrb on 2010-08-06
Sorry for reviving an old thread, but rajmahendra, were you able to fix this issue. I'm having the same problem on my laptop. I use the same .conkyrc and scripts on my desktop and no small rectangles are appearing at the end of the lines.

Let me know if you did find a solution! Thanks!

---

### Post by craig1234 on 2012-12-08
Sorry for reviving an old thread, but I stumbled upon this when I had this problem and it was never solved. 

The problem occurs when you edit or copy text from a file that was created in Windows or if text is copied over VNC. In these cases the text format changes and it automatically append an end of line character, which is invisible in most text editors. This is what causes the annoying square boxes you see in Conky. 

**To solve the problem**; create a NEW FILE in Leafpad and copy and paste your conky config. Then save the new file. This will remove the end of line characters and conky will run as normal. :p

---

