---
title: "wvdial and Huawei 3G Dongle"
date: 2009-08-08
forum: General Help
---

### Post by markytheone on 2009-08-08
I have searched all over for a wvdial.conf that works and I the furthest I can get is:

wvdial internet
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","three.co.uk"
AT+CGDCONT=1,"IP","three.co.uk"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 236800
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Aug  8 14:07:43 2009
--> Pid of pppd: 3277
--> Using interface ppp0
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> local  IP address 10.123.69.63
--> pppd: P[0c][06][08]Ø[07][06][08]
--> remote IP address 10.64.64.64
--> pppd: P[0c][06][08]Ø[07][06][08]
--> primary   DNS address 172.31.76.69
--> pppd: P[0c][06][08]Ø[07][06][08]
--> secondary DNS address 172.31.140.69
--> pppd: P[0c][06][08]Ø[07][06][08]

Then it just stalls. any ideas what is going on?

Thanks

Mark

---

### Post by There Was A Time on 2009-08-08
If you're using a Three Modem, you should just be able to set it up with " System > Preferences > Network Connections". That works from Hardy 8.04 onwards, IIRC. Sorry if you're aware of this.

---

### Post by markytheone on 2009-08-08
Sorry should have said, im on Hardy Server so no GUI.

Thanks

---

### Post by harry2006 on 2009-08-08
you mean even after getting this far, you are not able to connect to internet? quite surprising! i use wvdial and i get similar messages while connecting but then i'm able to connect to the internet once i reach this far. b'coz if its not able to connect to the ISP's server then it should not show those IPs, right?

---

### Post by garikaib on 2009-08-08
> **markytheone said:**
> I have searched all over for a wvdial.conf that works and I the furthest I can get is:

wvdial internet
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","three.co.uk"
AT+CGDCONT=1,"IP","three.co.uk"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 236800
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Aug  8 14:07:43 2009
--> Pid of pppd: 3277
--> Using interface ppp0
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> pppd: P[0c][06][08]Ø[07][06][08]
--> local  IP address 10.123.69.63
--> pppd: P[0c][06][08]Ø[07][06][08]
--> remote IP address 10.64.64.64
--> pppd: P[0c][06][08]Ø[07][06][08]
--> primary   DNS address 172.31.76.69
--> pppd: P[0c][06][08]Ø[07][06][08]
--> secondary DNS address 172.31.140.69
--> pppd: P[0c][06][08]Ø[07][06][08]

Then it just stalls. any ideas what is going on?

Thanks

Mark

Everything is just fine. All you need to do is tell Ubuntu that you want your internet connection to be the default root. Try the following when the above appears on the scren.

1) Press Ctrl+z  This sends wvdial into the background.

2) route add default ppp0   ie make ppp0 the default route

3) Ping google.com you should be able to do so.

---

### Post by Disco Elephant on 2009-08-09
> **markytheone said:**
> **Then it just stalls**. any ideas what is going on?

Try running it in the background, by appending an & to the end of the command line. It looks like wvdial is connecting, but it needs to keep running, so it doesn't return to the command prompt. Running it in the background will make the command prompt return immediately, while wvdial connects. 

You're also having the same problem I'm having, it's giving you a 10.X.X.X private IP address. Does anyone know how to make it connect with a public IP address? My modem does receive a public IP address when I connect with the windows client under XP.

---

