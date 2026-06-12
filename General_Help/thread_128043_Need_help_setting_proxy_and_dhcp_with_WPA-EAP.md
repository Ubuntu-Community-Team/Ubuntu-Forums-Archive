---
title: "Need help setting proxy and dhcp with WPA-EAP"
date: 2006-02-10
forum: General Help
---

### Post by Paloseco on 2006-02-10
I am trying to connect to a WPA-EAP connection so I have followed this [WPAHowto]("https://wiki.ubuntu.com/WPAHowto"). I have configured the files as if I only had one network, the wifi, named eth0. There are my configurations:


/etc/wpa_supplicant.conf
> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1

network={
ssid="udcwifi"
key_mgmt=WPA-EAP
pairwise=TKIP
group=TKIP
eap=TTLS
identity="user@domain"
password="mypass"
priority=2
}

/etc/network/interfaces
> 
  # eth0 is the wifi, eth1 does not exist
  auto lo eth1
  iface eth0 inet dhcp
  pre-up /etc/init.d/wpasupplicant start
  pre-up sleep 5

/sbin/wpa_action
> #! /bin/bash 

  IFNAME=$1
  CMD=$2

  if [ "$CMD" == "CONNECTED" ]; then
    SSID=`wpa_cli -i$IFNAME status | grep ^ssid= | cut -f2- -d=`
    logger "WiFi: Connecting `$IFNAME' to network `$SSID'"
    ifup $IFNAME
  elif [ "$CMD" == "DISCONNECTED" ]; then
    logger "WiFi: Disconnecting `$IFNAME'"
    ifdown $IFNAME
  fi

/etc/init.d/wpasupplicant> case "$1" in
	start)
		echo -n "Starting wpa_supplicant: "
		start-stop-daemon --start --name $PNAME \
			--oknodo --startas $DAEMON -- -B $OPTIONS
		sleep 1
		wpa_cli -a/sbin/wpa_action -B
		echo "done."
		;;
	stop)
		echo -n "Stopping wpa_supplicant: "
		start-stop-daemon --stop --name $PNAME \
			--oknodo
		echo "done."
		if [ -f $PIDFILE ]; then
			rm -f $PIDFILE;
		fi		
		;;



If I run manually wpa_supplicant with the arguments it seems to connect properly because the log ends like that:> PA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (auth)
EAPOL: External notification - portValid=1
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: authWhile --> 0
EAPOL: idleWhile --> 0


The iwconfig command shows:> root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"udcwifi"
          Mode:Managed  Frequency:2.472 GHz  Access Point: xx:xx:xx:xx:xx:xx
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key: "the key"   Security mode:open
          Power Management:off
          Link Quality=53/100  Signal level=-69 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

The IP is given by the Access Point. After restarting ubuntu I run kwifimanager and the green bar is 100% full and says connected but says also: Local IP: Unavailable. (so I think that ubuntu should ask for a IP to the AP and does not do that, correct me if I am wrong.)

I have to connect thru the proxy "proxy-wifi.ucv.udc.es" Port:3128. I set this in konqueror and Firefox but says that the proxy is unreachable. Can someone help me? I think I am about to achieve it!!

---

### Post by Paloseco on 2006-02-13
No ideas? :rolleyes:

---

### Post by Paloseco on 2006-02-14
Well guys, finally I got it working. I just have to run "dhclient eth0" each time I connect to wireless. Can someone tell me why this does not work automatically or how can I configure it to run by its own?

---

