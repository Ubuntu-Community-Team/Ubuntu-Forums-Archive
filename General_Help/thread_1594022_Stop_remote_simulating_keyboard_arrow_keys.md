---
title: "Stop remote simulating keyboard arrow keys"
date: 2010-10-11
forum: General Help
---

### Post by VH-BIL on 2010-10-11
I have updated to 10.10 and now my ir remote is simulating keyboard arrow keys which is causing problems in applications like Boxee. The weird thing is if I stop lircd it still simulates the keyboard arrow keys.

Does anyone know how to stop the keyboard arrow keys from triggering when the ir remote up, down, left or right buttons are pressed?

(Here are all the IR config files)

hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

lirc.conf
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Streamzap PC Remote remote:
include "/usr/share/lirc/remotes/streamzap/lircd.conf.streamzap"
```

lircd.conf.streamzap
```
#
# this config file was automatically generated
# using lirc-0.7.1-CVS(serial) on Fri Feb  4 23:20:56 2005
#
# contributed by Christoph Bartelmus
#
# brand:                       Streamzap
# model no. of remote control: PC Remote
# devices being controlled by this remote: USB receiver
#

begin remote

  name  Streamzap_PC_Remote
  bits            6
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           889  889
  zero          889  889
  plead         889
  pre_data_bits   8
  pre_data       0xA3
  gap          108344
  toggle_bit      2


      begin codes
          0                        0x00
          1                        0x01
          2                        0x02
          3                        0x03
          4                        0x04
          5                        0x05
          6                        0x06
          7                        0x07
          8                        0x08
          9                        0x09
          POWER                    0x0A
          MUTE                     0x0B
          CH_UP                    0x0C
          VOL_UP                   0x0D
          CH_DOWN                  0x0E
          VOL_DOWN                 0x0F
          UP                       0x10
          LEFT                     0x11
          OK                       0x12
          RIGHT                    0x13
          DOWN                     0x14
          MENU                     0x15
          EXIT                     0x16
          PLAY                     0x17
          PAUSE                    0x18
          STOP                     0x19
          |<<                      0x1A
          >>|                      0x1B
          RECORD                   0x1C
          <<                       0x1D
          >>                       0x1E
          RED                      0x20
          GREEN                    0x21
          YELLOW                   0x22
          BLUE                     0x23
      end codes

end remote

```

.lircrc
```
##########################################
# IREXEC
begin
   prog = irexec
   button = POWER
   config = poweroff
end
##########################################
# MPLAYER
begin
	prog = mplayer
	button = VOL_UP
	config = volume +1
	repeat = 1
end
begin
	prog = mplayer
	button = VOL_DOWN
	config = volume -1
	repeat = 1
end
begin
	prog = mplayer
	button = MUTE
	config = mute
end
begin
	prog = mplayer
	button = PAUSE
	config = pause
end
begin
	prog = mplayer
	button = PLAY
	config = seek +0
end
begin
	prog = mplayer
	button = STOP
	config = quit
end
begin
	prog = mplayer
	button = EXIT
	config = get_time_pos
	#config = get_property stream_pos
end
begin
	prog = mplayer
	button = >>
	config = seek +30
end
begin
	prog = mplayer
	button = <<
	config = seek -30
end
begin
	prog = mplayer
	button = >>|
	config = seek_chapter +1 0
end
begin
	prog = mplayer
	button = |<<
	config = seek_chapter -1 0
end
begin
	prog = mplayer
	button = RIGHT
	config = seek +60
end
begin
	prog = mplayer
	button = LEFT
	config = seek -60
end
begin
	prog = mplayer
	button = CH_UP
	config = audio_delay 0.1
end
begin
	prog = mplayer
	button = CH_DOWN
	config = audio_delay -0.1
end
begin
	prog = mplayer
	button = RED
	config = vo_fullscreen
end
begin
	prog = mplayer
	button = GREEN
	config = osd 3
	config = osd 1
end
begin
	prog = mplayer
	button = BLUE
	config = vobsub_lang 1
	config = vobsub_lang
end
begin
	prog = mplayer
	button = YELLOW
	config = osd_show_property_text "${filename}" 2400
	config = osd_show_text ""
end
begin
	prog = mplayer
	button = 0
	config = seek +99999
end
begin
	prog = mplayer
	button = 7
	config = seek -2
end
begin
	prog = mplayer
	button = 9
	config = seek +2
end
##########################################
# VLC
begin
	prog = vlc
	button = VOL_UP
	config = key-vol-up
	repeat = 1
end
begin
	prog = vlc
	button = VOL_DOWN
	config = key-vol-down
	repeat = 1
end
begin
	prog = vlc
	button = MUTE
	config = key-vol-mute
end
begin
	prog = vlc
	button = PLAY
	config = key-play-pause
end
begin
	prog = vlc
	button = PAUSE
	config = key-play-pause
end
begin
	prog = vlc
	button = STOP
	config = key-stop
end
begin
	prog = vlc
	button = >>
	config = key-jump+medium
end
begin
	prog = vlc
	button = <<
	config = key-jump-short
end
begin
	prog = vlc
	button = >>|
	config = key-next
end
begin
	prog = vlc
	button = |<<
	config = key-prev
end
begin
	prog = vlc
	button = UP
	config = key-nav-up
end
begin
	prog = vlc
	button = DOWN
	config = key-nav-down
end
begin
	prog = vlc
	button = LEFT
	config = key-lav-left
end
begin
	prog = vlc
	button = RIGHT
	config = key-right
end
begin
	prog = vlc
	button = CH_UP
	config = key-audiodelay-up
end
begin
	prog = vlc
	button = CH_DOWN
	config = key-audiodelay-down
end
begin
	prog = vlc
	button = BLUE
	config = key-crop
end


```

Lircmap.xml (Boxee)
```
<lircmap>
	<remote device="Streamzap_PC_Remote">
		<pause>PAUSE</pause>
		<stop>STOP</stop>
		<forward>&gt;&gt;</forward>
		<reverse>&lt;&lt;</reverse>
		<left>LEFT</left>
		<right>RIGHT</right>
		<up>UP</up>
		<down>DOWN</down>
		<select>OK</select>
		<pageplus>CH_UP</pageplus>
		<pageminus>CH_DOWN</pageminus>
		<back>EXIT</back>
		<menu>MENU</menu>
		<title>PLAY</title>
		<info>More</info>
		<skipplus>&gt;&gt;|</skipplus>
		<skipminus>|&lt;&lt;</skipminus>
		<display>Teletext</display>
		<start>Home</start>
		<record>RECORD</record>
		<volumeplus>VOL_UP</volumeplus>
		<volumeminus>VOL_DOWN</volumeminus>
		<mute>MUTE</mute>
		<power>POWER</power>
		<myvideo>Videos</myvideo>
		<mymusic>Music</mymusic>
		<mypictures>Pictures</mypictures>
		<mytv>TV</mytv>
		<one>1</one>
		<two>2</two>
		<three>3</three>
		<four>4</four>
		<five>5</five>
		<six>6</six>
		<seven>7</seven>
		<eight>8</eight>
		<nine>9</nine>
		<zero>0</zero>
		<mytv>RED</mytv>
		<mymusic>GREEN</mymusic>
		<mypictures>YELLOW</mypictures>
		<myvideo>BLUE</myvideo>
	</remote>
</lircmap>

```

---

### Post by straxus on 2010-10-13
I have the same remote, and the same problem.  I've worked around it for now by commenting out the directional buttons in my config files, but a real fix would be most welcome.

I've also noticed that the Power button on the remote is triggering a key press as well.  I'm not 100% certain which key, but I strongly suspect it's PrtScr.

---

### Post by VH-BIL on 2010-10-13
> **straxus said:**
> I've worked around it for now by commenting out the directional buttons in my config files, but a real fix would be most welcome.

That is what I have done.

There is a kernel module now so having lirc installed means you have two instanced of it. I uninstalled lirc and did a lsmod and streamzap and some other stuff relating to lirc was there.

I did a "sudo rmmod streamszap" after reinstalling lirc and it resolved the problem but do not know how to make it permanent, as the lirc kernel module reloads after a reboot.

---

