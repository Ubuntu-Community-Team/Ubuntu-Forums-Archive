---
title: "Conky keeps trying MPD at localhost (python-mpd)"
date: 2010-03-05
forum: General Help
---

### Post by sibble on 2010-03-05
First off let me say that MPD is working and I can connect to it with my iPod, as well as using Ario on the same machine that it's running from.

Here is the python script Conky is using to connect to MPD:
```

#!/usr/bin/env python
#------------------------------------------------#
#mpd notify-osd & cover linking for conky
#v1.2 sen
#------------------------------------------------#
#dependencies: python-mpd, (libnotify, notify-osd)
#------------------------------------------------#
import mpd,os,time
home = os.path.expanduser('~')

# settings
mpd_dir = '/var/lib/mpd/music/'							#mpd music directory
notify_osd = True								#enable/disable notify-osd 
conky = True									#enable/disable conky cover linking
cover_default = '/home/sen/.icons/yamaha.svg'	#default cover for notify-osd
		
# notify-osd output
def notify(cover,artist,album,title):
	os.system('notify-send -i "%s" "%s" "%s\n%s"'%(cover,title,artist,album))

# look for cover
def coverPath():
	cover = cover_default
	
	# look in ~/.covers
	if os.path.exists('%s/.covers/%s-%s.jpg'%(home,artist,album)):
		cover = '%s/.covers/%s-%s.jpg'%(home,artist,album)
	
	# look in album dir
	else:
		for img in('cover.jpg', 'folder.jpg', 'front.jpg', 'album.jpg'):
			if os.path.exists('%s%s/%s'%(mpd_dir,os.path.dirname(last_song),img)):
				cover= '%s%s/%s'%(mpd_dir,os.path.dirname(last_song),img)
				break
	
	# link cover to /tmp for conky
	if conky == True:
		try:
			if os.path.exists('/tmp/cover'):
				os.system('rm /tmp/cover')
			if cover != cover_default:
				os.system('ln -s "%s" /tmp/cover'%cover)
		except:
			pass
			
	return cover

# mpd status message
def action(status):
	if status == 'play':
		bubble = 'notification-audio-play' + ' MPD Playing'
		notify(coverPath(),artist,album,title)
	elif status == 'pause':
		bubble = 'notification-audio-pause' + ' MPD Paused'
	else:
		bubble = 'notification-audio-stop' + ' MPD Stopped'
	os.popen('notify-send -u critical -h string:x-canonical-private-icon-only: -h string:x-canonical-private-synchronous: -i %s'%bubble)

# connect to MPD
success = False
while success == False:
	try:
		client = mpd.MPDClient()
		client.connect('bbox-sib', 6600) 
		success = True
	except:
		print 'connection to MPD could not be established'
		time.sleep(5)
		success = False

try:
	last_song = client.currentsong()['file']
	last_status = client.status()['state']
	artist = client.currentsong()['artist']
	album = client.currentsong()['album']
	title = client.currentsong()['title']
	cover = coverPath()
	if notify_osd == True:
		notify(cover,artist,album,title)
	
except:
	last_song = ""
	last_status = ""

while True:
	try:
		currentsong = client.currentsong()['file']
		status = client.status()['state']
	except:
		currentsong = last_song
		status = last_status

	if last_status <> status:
		try:
			last_status = client.status()['state']
			if notify_osd == True:
				action(status)
		except:
			pass

	if last_song <> currentsong and status == 'play':
		try:
			last_song = client.currentsong()['file']
			try:
				artist = client.currentsong()['artist']
			except:
				artist = 'Unknown'
			try:
				album = client.currentsong()['album']
			except:
				album = 'Unknown'
			try:
				title = client.currentsong()['title']
			except:
				title = 'Unknown'
			cover = coverPath()
			if notify_osd == True:
				notify(cover,artist,album,title)
		except:
			pass
			
	time.sleep(1)

```

Next, here is my mpd.conf:

```

music_directory		"/var/lib/mpd/music"
playlist_directory		"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file			"/var/log/mpd/mpd.log"
pid_file			"/var/run/mpd/pid"
state_file			"/var/lib/mpd/state"

user				"mpd"
bind_to_address		"bbox-sib"
port				"6600"
log_level			"default"

save_absolute_paths_in_playlists	"no"

follow_outside_symlinks	"yes"
follow_inside_symlinks		"yes"

zeroconf_enabled		"yes"
zeroconf_name			"Music Player"

default_permissions             "read,add,control,admin"

input {
        plugin "curl"
}

audio_output {
        type      "ao"
        driver    "oss"
        options   "" 
        name      "oss"
}

filesystem_charset		"UTF-8"
id3v1_encoding			"UTF-8"

```

And last, here's my hosts file:
```

127.0.0.1	localhost
# 127.0.1.1	bbox-sib
192.168.222.137 bbox-sib

# ::1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

On the same machine MPD is running on, I'm using Ario to connect to it @ bbox-sib:6600.  In mpd_infos.py, you can see I'm also attempting to connect to bbox-sib:6600.  However, this is error I'm getting from Conky:
```
Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection Refused.
```

Any direction here would be greatly appreciated :)  Thanks!

---

### Post by sibble on 2010-03-05
[http://wiki.archlinux.org/index.php/MPD](http://wiki.archlinux.org/index.php/MPD)
> Binding to address and port causing problems in mpd-0.14.2 best to leave commented.

Commented out the address bind, all is working perfectly now.

---

