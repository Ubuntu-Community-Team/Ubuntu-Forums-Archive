---
title: "Conky issues after re-install"
date: 2010-01-23
forum: General Help
---

### Post by Admiral Yi on 2010-01-23
Hello,
Just updated to 9.04 from 8.10. I reinstalled using the disk and kept my home partition with my .conkyrc in it. I installed conky, and then added to my list of startup programs as normal. When i login conky comes up and everything works fine, but it is on top of all other windows when it wasn't before. If I kill it and start it again, then it is behind the other windows as it should be, but then my 'hddtemp' commands don't work. I'll post my config below so you can have a look at it. Any help is appreciated. 

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Trebuchet MS:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 315 5
maximum_width 315

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 70
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player none

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
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
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
${font Trebuchet MS:size=9}${color #55D036}      $sysname $kernel $machine - $nodename 
${color #FFFFFF}       Uptime:${color lightgrey} $uptime ${color #FFFFFF} Load:${color lightgrey} $loadavg

${font Kochi Mincho MS:size=12}${color #55D036}System Info ${hr 2}
${font Trebuchet MS:size=8}${color #FFFFFF}Temperatures:
${color #FFFFFF}Core 0 Temp:    ${color lightgrey}${execi 8 sensors | grep -A 1 'Core 0' | cut -c14-21 | sed '/^$/d'}  ${alignr}${color #FFFFFF}Core 1 Temp:    ${color lightgrey}${execi 8 sensors | grep -A 1 'Core 1' | cut -c14-21 | sed '/^$/d'}
${color #FFFFFF}Core 2 Temp:    ${color lightgrey}${execi 8 sensors | grep -A 1 'Core 2' | cut -c14-21 | sed '/^$/d'}  ${alignr}${color #FFFFFF}Core 3 Temp:    ${color lightgrey}${execi 8 sensors | grep -A 1 'Core 3' | cut -c14-21 | sed '/^$/d'}
${color #FFFFFF}GPU Temp:        +${color lightgrey}${execi 1 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c46-47}.0°C ${alignr}${color #FFFFFF}Sda Temp:            ${color lightgrey}+${execpi 8 sudo hddtemp /dev/sda | cut --characters 31-35 | xargs ~/Scripts/ColorTempHDD.sh}
${color #FFFFFF}Sdb Temp:            ${color lightgrey}+${execpi 8 sudo hddtemp /dev/sdb | cut --characters 28-32 | xargs ~/Scripts/ColorTempHDD.sh}

${color #FFFFFF}CPUs:
${color #FFFFFF}Usage:${color #FFFFFF} ${color lightgrey}${cpu}% ${color #FFFFFF}${cpubar}
${color #FFFFFF}${cpugraph 55D036 55D036}
${color #FFFFFF}Processes:${color lightgrey} $processes  ${color #FFFFFF}Running:${color lightgrey} $running_processes ${color #FFFFFF}

${color #FFFFFF}Memory:
${color #FFFFFF}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #FFFFFF}${membar 5,110}
${color #FFFFFF}   Buffered Mem:${color lightgrey} $buffers              
${color #FFFFFF}   Cached Mem:   ${color lightgrey} $cached 
${color #FFFFFF}Swap:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #FFFFFF}${swapbar 5,110}

${color #FFFFFF}Hard Disks:
${color #FFFFFF} Root ${color lightgrey}${fs_used /}/${fs_size /} - ${fs_used_perc /}%${alignr}${color #FFFFFF}${fs_bar 5,120 /}
${color #FFFFFF} Home ${color lightgrey}${fs_used /home}/${fs_size /home} - ${fs_used_perc /home}%${alignr}${color #FFFFFF}${fs_bar 5,120 /home}

${color #FFFFFF}Disk IO: ${color lightgrey}$diskio 
${color #FFFFFF}${diskiograph 55D036 55D036}

${font Kochi Mincho MS:size=12}${color #55D036}Top ${hr 2}
${font Bitstream Vera Sans Mono:size=8}${color #FFFFFF}CPU Usage         PID     CPU% 
${color #55D036} ${top name 1} ${top pid 1} ${top cpu 1} 
${color #FFFFFF} ${top name 2} ${top pid 2} ${top cpu 2}
${color #FFFFFF} ${top name 3} ${top pid 3} ${top cpu 3}
${color #FFFFFF} ${top name 4} ${top pid 4} ${top cpu 4}
${color #FFFFFF} ${top name 5} ${top pid 5} ${top cpu 5}

${color #FFFFFF}Mem Usage         PID     MEM%
${color #55D036} ${top_mem name 1} ${top_mem pid 1} ${top_mem mem 1}
${color #FFFFFF} ${top_mem name 2} ${top_mem pid 2} ${top_mem mem 2}
${color #FFFFFF} ${top_mem name 3} ${top_mem pid 3} ${top_mem mem 3}
${color #FFFFFF} ${top_mem name 4} ${top_mem pid 4} ${top_mem mem 4}
${color #FFFFFF} ${top_mem name 5} ${top_mem pid 5} ${top_mem mem 5}

${font Kochi Mincho MS:size=12}${color #55D036}Network ${hr 2}
${font Trebuchet MS:size=8}${color #FFFFFF}Local:          ${color lightgrey}${addr eth0}${alignr}${color #FFFFFF}${execpi 10 ~/Scripts/pingtest.sh 192.168.0.2}
${color #FFFFFF}Laptop:       ${color lightgrey}192.168.0.3        ${alignr}${color #FFFFFF}${execpi 10 ~/Scripts/pingtest.sh 192.168.0.3}

${color #FFFFFF}Down:${color lightgrey} ${downspeedf eth0} k/s $alignr${color #FFFFFF} Up:${color lightgrey} ${upspeedf eth0} k/s
${color #FFFFFF}${downspeedgraph eth0 27,120 55D036 55D036 180} $alignr${color #FFFFFF}${upspeedgraph eth0 27,120 55D036 55D036 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color #FFFFFF}Port(s)${alignr}#Connections
${color #FFFFFF}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color #FFFFFF}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color #FFFFFF}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${font Kochi Mincho MS:size=12}${color #55D036}  	         Time Remaining
${font Trebuchet MS:size=11}${color #FFFFFF}${execi 1 sh  /home/joseph/Scripts/date-calc.sh}
```

---

### Post by Admiral Yi on 2010-01-23
Surely someone can help?

---

