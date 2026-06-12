---
title: "simple firewall"
date: 2006-03-05
forum: General Help
---

### Post by pbransford on 2006-03-05
Well, get "lokkit" installed first off, and then modify your /etc/init.d/networking file to launch lokkit at appropriate times, enabling and disabling as needed.

Just remember to save the old file, and reverse the changes if you remove lokkit. The commands I used are -q for quiet (no prompting... otherwise you get an ncurses config dialog every boot...), --high (high security. basically nothing comes in unless related to outgoing.) and --dhcp (allows incoming dhcp. needed if you use dhcp to configure your interfaces, otherwise you may remove for added security). --disabled flushes the iptables rules.
 
For example, here is mine with modifications in bold type. (there are 8)
Works like a charm, "sudo iptables -L" after appropriate start/stopping of the script verifies.

```

#!/bin/sh
#
# manage network interfaces and configure some networking options

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

if ! [ -x /sbin/ifup ]; then
    exit 0
fi

[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

spoofprotect_rp_filter () {
    # This is the best method: turn on Source Address Verification and get
    # spoof protection on all current and future interfaces.
    
    if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]; then
        for f in /proc/sys/net/ipv4/conf/*/rp_filter; do
            echo 1 > $f
        done
        return 0
    else
        return 1
    fi
}


spoofprotect () {
    if [ "$VERBOSE" != no ]; then
        log_begin_msg "Setting up IP spoofing protection..."
        spoofprotect_rp_filter
        log_end_msg $?
    else
        if ! spoofprotect_rp_filter; then
	    log_failure_msg "Failed to setup IP spoofing protection"
	fi
    fi
}

ip_forward () {
    if [ -e /proc/sys/net/ipv4/ip_forward ]; then
        if [ "$VERBOSE" != no ]; then
            log_begin_msg "Enabling packet forwarding..."
            echo 1 > /proc/sys/net/ipv4/ip_forward
            log_end_msg $?
        else
            echo 1 > /proc/sys/net/ipv4/ip_forward
        fi
    fi
}

syncookies () {
    if [ -e /proc/sys/net/ipv4/tcp_syncookies ]; then
        if [ "$VERBOSE" != no ]; then
            log_begin_msg "Enabling TCP/IP SYN cookies..."
            echo 1 > /proc/sys/net/ipv4/tcp_syncookies
            log_end_msg $?
        else
            echo 1 > /proc/sys/net/ipv4/tcp_syncookies
        fi
    fi
}

doopt () {
    optname=$1
    default=$2
    opt=`grep "^$optname=" /etc/network/options`
    if [ -z "$opt" ]; then
        opt="$optname=$default"
    fi
    optval=${opt#$optname=}
    if [ "$optval" = "yes" ]; then
        eval $optname
    fi
}

case "$1" in
    start)
	doopt spoofprotect yes
        doopt syncookies no
        doopt ip_forward no

        log_begin_msg "Configuring network interfaces..."
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
        if [ "$VERBOSE" != no ]; then
            ifup -a
            **lokkit -q --high --dhcp**
        else
            ifup -a >/dev/null 2>&1
            **lokkit -q --high --dhcp**
        fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	log_end_msg $?
	;;
    stop)
        if sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\1 \2/p' /proc/mounts | 
          grep -q "^/ nfs$"; then
            log_failure_msg "NOT deconfiguring network interfaces: / is an NFS mount"
        elif sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\1 \2/p' /proc/mounts |  
          grep -q "^/ smbfs$"; then
            log_failure_msg "NOT deconfiguring network interfaces: / is an SMB mount"
	elif sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\2/p' /proc/mounts | 
          grep -qE '^(nfs[1234]?|smbfs|ncp|ncpfs|coda|cifs)$'; then
            log_failure_msg "NOT deconfiguring network interfaces: network shares still mounted."
        else
            log_begin_msg "Deconfiguring network interfaces..."
            if [ "$VERBOSE" != no ]; then
                ifdown -a --exclude=lo
		**lokkit -q --disabled**
            else
                ifdown -a --exclude=lo >/dev/null 2>&1
		**lokkit -q --disabled**
            fi
	    log_end_msg $?
        fi
	;;
    force-reload|restart)
	doopt spoofprotect yes
        doopt syncookies no
        doopt ip_forward no
        log_begin_msg "Reconfiguring network interfaces..."
        if [ "$VERBOSE" != no ]; then
            ifdown -a --exclude=lo
            **lokkit -q --disabled**
            ifup -a
            **lokkit -q --high --dhcp**
        else
            ifdown -a --exclude=lo >/dev/null 2>&1
            **lokkit -q --disabled**
            ifup -a > /dev/null 2>&1
            **lokkit -q --high --dhcp**
        fi
	log_end_msg $?
	;;
    *)
	log_success_msg "Usage: /etc/init.d/networking {start|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0

```


... would you believe me if I told you I'm still fairly new to linux? I'm getting there though...

---

### Post by handy on 2006-03-05
This may or may not be worth a read for you? :

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by pbransford on 2006-03-05
Hehe, thanks, but I should mention that I'm a slashdot reader and have been properly indoctrinated into anti-MSism...

---

### Post by GTvulse on 2006-03-06
[quote=pbrandsford]... would you believe me if I told you I'm still fairly new to linux? I'm getting there though...[/quote]

And it shows... ;-) What you suggest to do above doesn't give you any gain and simply creates a new layer of complexity.

lokkit is a simple-minded iptables script generator frontend. **You don't need to load it at startup every time!!!!!!!**. There is already a lokkit sysinit script, (check /etc/init.d/) that manages the actual iptables commands contained in a script called /etc/defaults/lokkit.

---

