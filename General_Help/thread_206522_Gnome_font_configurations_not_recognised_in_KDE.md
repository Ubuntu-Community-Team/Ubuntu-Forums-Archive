---
title: "Gnome font configurations not recognised in KDE"
date: 2006-06-30
forum: General Help
---

### Post by barisurum on 2006-06-30
Hi there,

   I use KDE as desktop and when I start a gnome application, the font configurations of gnome is not recognised which are much more smaller than shown. I run "sudo gnome-font-properties" and they get back to normal sizes which I had configured when I was using gnome.
  Do I have to run this everytime or is there a permanent fix for this?
  Thankx

---

### Post by ayoli on 2006-06-30
gnome-settings-deamon doesn't start since you're using KDE, so try to add it in your startup apps in kde, or in your /etc/init.d/rc.local:
```
/usr/lib/control-center/gnome-settings-daemon
```

---

### Post by barisurum on 2006-06-30
It doesnt seem to fix it or I did something wrong. Here is my rc.local:

  > PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
[COLOR="Red"]**/usr/lib/control-center/gnome-settings-daemon**[/COLOR]


---

### Post by barisurum on 2006-06-30
pleeese where should I put this line?

---

### Post by tflanders on 2006-07-07
I put mine in the startx script

---

