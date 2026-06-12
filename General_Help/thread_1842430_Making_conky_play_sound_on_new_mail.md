---
title: "Making conky play sound on new mail"
date: 2011-09-11
forum: General Help
---

### Post by sbjaved on 2011-09-11
Hi,

have my conky setup to play sound when new mail arrives. Its a script that basically checks if inbox unread count is more than 1 or not; if it is, it plays a sound. Problem is that the conky runs the script periodically (every 60 secs) and it will keep playing the sound for the same unread mail over and over again. Is it possible to have it play sound for *new* email only?

---

### Post by Habitual on 2011-09-11
Post the conky code/source...

---

### Post by Habitual on 2011-09-11
Edit:

unread mail is technically new email, wouldn't you think?

---

### Post by sbjaved on 2011-09-11
> **Habitual said:**
> Edit:

unread mail is technically new email, wouldn't you think?
Right. But you already know there is an unread email. You don't want to be beeped every 60 secs :)
> 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer none
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 500

#text_buffer_size 1024

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
xftfont Droid Sans Mono:size=9
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_inner_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 15
gap_y 20

# stuff after &#8216;TEXT&#8217; will be formatted on screen

TEXT
$color
${color 85A93C}SYSTEM ${hr 2}$color
$nodename $sysname $kernel
Total time online $uptime
Conky $conky_version
${font size=10}${exec date +"%d-%b-%Y"}$font
${time %r}

${color 85A93C}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${if_match ${hwmon temp 1} <= 50}${color green}${font size=10}${hwmon temp 1}C$font${color}${endif}${if_match ${hwmon temp 1} >= 51}${if_match ${hwmon temp 1} <=70}${color yellow}${font size=10}${hwmon temp 1}C$font${color}${endif}${endif}${if_match ${hwmon temp 1} >= 71}${if_match ${hwmon temp 1} <=89}${color orange}${font size=10}${hwmon temp 1}C$font${color}${endif}${endif}${if_match ${hwmon temp 1} >= 90}${color red}${font size=10}${hwmon temp 1}C$font${color}${endif}
$cpubar
${cpugraph 000000 ffffff}

${color 85A93C}BATTERY:$color ${if_match ${battery_percent BAT0} <= 9}${color red}${font size=10}${battery_percent BAT0}%$font${color} ${battery_bar BAT0}${endif}${if_match ${battery_percent BAT0} >= 10}${if_match ${battery_percent BAT0} <=49}${color orange}${font size=10}${battery_percent BAT0}%$font${color} ${battery_bar BAT0}${endif}${endif}${if_match ${battery_percent BAT0} >= 50}${if_match ${battery_percent BAT0} <=79}${color yellow}${font size=10}${battery_percent BAT0}%$font${color} ${battery_bar BAT0}${endif}${endif}${if_match ${battery_percent BAT0} >= 80}${if_match ${battery_percent BAT0} <=99}${color green}${font size=10}${battery_percent BAT0}%$font${color} ${battery_bar  BAT0}${endif}${endif}${if_match ${battery_percent BAT0} >= 100}${font size=10}${battery_percent BAT0}%$font ${battery_bar BAT0}${endif}
Remaining: ${font size=10}${execi 10 acpi -b | grep "Battery" | awk '{print $5}' | cut -c 1-5} min$font

${color 85A93C}SYSTEM MONITOR ${hr 2}$color
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color 85A93C}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Root: ${fs_free /} ${fs_bar 6 /}$color

${color 85A93C}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} /s ${alignr}Up: ${upspeed wlan0} /s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
Public IP: ${execi 60 /home/saad/conkyIp}
Signal: ${font size=10}${wireless_link_qual wlan0}%$font

${color 85A93C}MAIL/SOCIAL ${hr 2}$color
${execpi 300 /home/saad/facebook notify}
${execpi 300 /home/saad/facebook message}
${execpi 300 /home/saad/facebook friend}
[B][COLOR="Red"]${execpi 60 /home/saad/gmail.sh}
[/COLOR][/B]
${color 85A93C}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

This is the gmail.sh script, which calls a python program for the actual mail checking:

> #!/bin/bash

x=$(python gmail_check.py [email]xxxxxx@gmail.com[/email] xxxxxxxx | grep -oE [[:digit:]])

if [ "$x" -eq "0" ]
then
	echo No New Email
else
	echo '${font size=10}${color ff0000}'$x'${color}$font' NEW EMAILS
	play -q /usr/share/sounds/gnome/default/alerts/drip.ogg
fi

Here is the gmail_check.py:

> import urllib2
import feedparser

from optparse import OptionParser

class Gmail:
    """ Provides interface for checking Google Mail
        For use with Conky
    """

    def __init__(self, username, password):
        self.username = username
        self.password = password
        self.url = 'https://mail.google.com/mail/feed/atom'
        self.passwd_mgr = self._password_manager()
        self.doc = None

    def _password_manager(self):
        """ Build and return a password manager
        """
        password_mgr = urllib2.HTTPPasswordMgrWithDefaultRealm()
        password_mgr.add_password(None, self.url, self.username, self.password)
        return password_mgr

    def _open_url(self):
        """ Using password manager open and read feed url over https
        """
        handler = urllib2.HTTPBasicAuthHandler(self.passwd_mgr)

        opener = urllib2.build_opener(handler)
        file = opener.open(self.url)
        return file.read()

    def _parse_atom(self):
        """ Open feed and parse atom using feedparser
        """
        file = self._open_url()
        self.doc = feedparser.parse(file)

    def get_mail_count(self):
        """ Return unread mail count
        """
        self._parse_atom()
        return len(self.doc['entries'])

    def get_mail_summary(self, number=3):
        """ Return summary of emails, containing from and subject
        """
        pass
#        entries = doc.entries
#        summaries = {}
#        if entries:
#            for x in range(3):
#                summaries[x] = {'from_address': entries[x]['author_detail']['email'],
#                    'from_name': entries[x]['author_detail']['name'],
#                    'title': entries[x]['title_detail']['value']}
#        return summaries


if __name__ == "__main__":
    usage = "usage: %prog [options] username password"
    parser = OptionParser(usage=usage)
    parser.add_option("-m", "--messages", action="store_true", dest="messages",
                      help="display message information", default=False)

    (options, args) = parser.parse_args()

    if len(args) < 2:
        parser.error("Please supply both username and password")

    mail = Gmail(username=args[0], password=args[1])

    print "Unread: %s" % mail.get_mail_count()

---

