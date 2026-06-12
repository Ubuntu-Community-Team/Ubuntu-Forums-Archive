---
title: "Problems with netconfig"
date: 2006-04-06
forum: General Help
---

### Post by jrios_03 on 2006-04-06
Hi, I'm back....

I got and ADSL connection in Ubuntu 5.10 Breezy, I have the ENL832-TX-ICNT network card and it's run perfectly... but when I try to configure it to run at boot, I have a little problem... the Readme File says:
```
c. automatically load and configure at next boot time

   -----------------------------------------------------

     c1. cp sundance.o /lib/modules/`uname -r`/kernel/drivers/net

     *note: The `uname -r` is a command. Don't replace `uname -r` with

            2.4.18, 2.4.20smp, or some others. Must type `uname -r` directly.



     c2. Add the following lines at /etc/modules.conf:

	           

	      alias eth0 sundance

	      options sundance <optional parameters>

	           	           

     c3. Run "netconfig" or "netconf" to create configuration script 



              ifcfg-eth0 located at /etc/sysconfig/network-scripts or 

              create it manually.

              [see - Configuration Script Sample]



     c4. Driver will automatically load and configure at 

              next boot time.

              

     c5. Configuration Script Sample

     ===============================

         Here is a sample of a simple configuration script:



         DEVICE=eth0

         USERCTL=no

         ONBOOT=yes

         POOTPROTO=none

         BROADCAST=207.200.5.255

         NETWORK=207.200.5.0

         NETMASK=255.255.255.0

         IPADDR=207.200.5.2
```
When I try to do the c3 point, the console return ```
root@ubuntu:~/Linux# netconfig
bash: netconfig: command not found
```

And when I try to download the netconfig teh console return```
root@ubuntu:~/Linux# apt-get install netconfig
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete netconfig
```

What I can do????

Please help me.....

Grettings from Chile:confused:

---

### Post by dcstar on 2006-04-07
[QUOTE=jrios_03]Hi, I'm back....

I got and ADSL connection in Ubuntu 5.10 Breezy, I have the ENL832-TX-ICNT network card and it's run perfectly... but when I try to configure it to run at boot, I have a little problem... the Readme File says:
.......
What I can do????

Please help me.....

Grettings from Chile:confused:[/QUOTE]
ifconfig is probably the closest command, but you may need to manually edit the /etc/network/interfaces file and put in the information your card needs to work.

Either that or: System-Administration-Networking and hopefully your network card is listed there ready to configure (this is the best method).

---

