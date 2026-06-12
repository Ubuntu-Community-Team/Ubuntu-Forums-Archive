---
title: "wifi problem hp pavilion zv5000"
date: 2012-04-30
forum: General Help
---

### Post by caste274 on 2012-04-30
hi,

I've installed Ubuntu in my hp pavilion zv5000, i'm trying to activate wifi , but it doesn't work. I read a lot of threads but nothing works.

Can you help me? thanks a lot!

This can give you information about my pc.

claudio@Sheldon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


claudio@Sheldon:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:0f:b0:08:b5:fe  
          Direc. inet:192.168.0.15  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::20f:b0ff:fe08:b5fe/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:24535 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:14753 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:33424284 (33.4 MB)  TX bytes:1754577 (1.7 MB)
          Interrupción:18 Dirección base: 0x7000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)


claudio@Sheldon:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


claudio@Sheldon:~$ lspci -vvnn | grep 14e4
02:02.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)

---

### Post by uylug on 2012-04-30
```
sudo ifconfig wlan0 up
```or
```
sudo ifup wlan0
```


Sorry for writing in another language but... de casualidad hablás español..?

---

### Post by gulmer on 2012-04-30
I've got the same netbook with a Broadcom BCM4306 WIFI card. My WIFI is working OK. First make sure the WIFI is turned on with the button for turning it on and off is engaged for on. Then in Synaptic Package Manager, with broadcom in search box, install the b-43-fwcutter. That's all I've got installed that got my WIFI working. After the fwcutter is installed, click on the WIFI icon on top panel and see if your wireless is enabled and working. You may have to run update manager and turn computer off and back on.

---

### Post by caste274 on 2012-05-02
uylug:

these are the results:

claudio@Sheldon:~$ sudo ifconfig wlan0 up
[sudo] password for claudio:
SIOCSIFFLAGS: Error desconocido 132
claudio@Sheldon:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

I speak Spanish, but I think that there are more possibilities to solve the problem if I write in English....


gulmer:

the button for turning the wifi on doesn't work in Ubuntu (in Windows XP it worked without problems).
I installed the b-43-fwcutter and did what you said before opening the thread, without success.

What can I do?

Thanks a lot!!

---

### Post by caste274 on 2012-05-07
does anyone have the same problem? :(

---

### Post by iw2198 on 2012-06-19
i had the same problem. i had to make sure my wifi adapter was turned on in windows. Then login to ubuntu. other than that it works fine.

---

### Post by TheMrOrange on 2012-06-19
Please, post the output of
ifconfig

---

### Post by charlie cat on 2012-06-19
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers)
Quick summary: Gulmer's on the right track, but you also have to install the package firmware-b43legacy-installer .

---

