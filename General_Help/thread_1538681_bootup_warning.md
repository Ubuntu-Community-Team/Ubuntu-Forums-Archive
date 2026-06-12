---
title: "bootup warning"
date: 2010-07-25
forum: General Help
---

### Post by MiTavis on 2010-07-25
I updated to 10.04 from 9:10 and after boot got the following error: 'An error occurred while mounting <<saned>> press S to skip mounting  or M for manual"

I found similar errors which led me to check the file fstab under root/etc and found the following:

odo, «saned» se inicia cuando inetd lo necesita cada vez que el cliente intenta conectarse al servidor;\n - como un demonio independiente, lanzado al inicio del sistema. En\neste modo «saned» se ejecuta en segundo plano por sí mismo y escucha conexiones de los clientes.\n\nEn modo independiente, «saned» se anuncia por sí mismo en la red y puede detectarse automáticamente por los clientes SANE sin configuración por parte de los mismos. Aun así, será necesario que configure el servidor para aceptar conexiones de los clientes.\n\nAcepte esta opción si desea utilizar esta característica.
Extended_description-eu.utf-8: Saned zerbitzariak, gaiturik dagoenean, eskanerrak sare biez eskuragarri egiten ditu.\n\nSaned exekutatzeko bi modu ezberdin daude:\n - inetd zerbitzu gisa, inetd superzerbitzariak abiarazia. 

I do not know where this came from and can not read it.

Any help?

I will try to comment it out in the terminal application

---

### Post by borth92 on 2010-07-25
> **MiTavis said:**
> I updated to 10.04 from 9:10 and after boot got the following error: 'An error occurred while mounting <<saned>> press S to skip mounting  or M for manual"

I found similar errors which led me to check the file fstab under root/etc and found the following:

odo, «saned» se inicia cuando inetd lo necesita cada vez que el cliente intenta conectarse al servidor;\n - como un demonio independiente, lanzado al inicio del sistema. En\neste modo «saned» se ejecuta en segundo plano por sí mismo y escucha conexiones de los clientes.\n\nEn modo independiente, «saned» se anuncia por sí mismo en la red y puede detectarse automáticamente por los clientes SANE sin configuración por parte de los mismos. Aun así, será necesario que configure el servidor para aceptar conexiones de los clientes.\n\nAcepte esta opción si desea utilizar esta característica.
Extended_description-eu.utf-8: Saned zerbitzariak, gaiturik dagoenean, eskanerrak sare biez eskuragarri egiten ditu.\n\nSaned exekutatzeko bi modu ezberdin daude:\n - inetd zerbitzu gisa, inetd superzerbitzariak abiarazia. 

I do not know where this came from and can not read it.

Any help?

I will try to comment it out in the terminal application


This is not much help but i put the spanish into google translate for you:

odo  'saned "inetd starts when you need it every time the client tries to  connect to the server, \ n - as a daemon, started at system startup. In  \ neste mode saned 'runs in the background by itself and listens for  connections from clients. \ N \ nThe independently, "saned" announces  itself on the network and can be detected automatically by customers  with no configuration SANE by them. Still, you will need to configure the server to accept client connections. \ N \ nAcepte this option to use this feature.
Extended_description-eu.utf-8:  Saned zerbitzariak, gaiturik dagoenean, Egito eskuragarri eskanerrak  Biez sare ditu. \ N \ Nsana exekutatzeko bi modu ezberdin Daude: \ n -  GISA Zerbitzu inetd, inetd superzerbitzariak abiarazia.

---

### Post by drs305 on 2010-07-25
Remove the entire entry from your /etc/fstab  I don't know how it got there but it definitely doesn't belong in fstab.

---

### Post by MiTavis on 2010-07-25
Thanks for the last reply. I will edit the file to remove everything. Note that i tried to put ## in front of the text above with the same error message occurring. I also found a folder in root with the name <<saned>>. Perhaps I need to remove that as well.

Note that the software is actually loaded on an 8 gig usb memory card. When I upgraded the version of Ubuntu I have on my USB hard drive, I did not get the issue.

---

