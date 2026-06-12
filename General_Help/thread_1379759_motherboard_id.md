---
title: "motherboard id"
date: 2010-01-12
forum: General Help
---

### Post by seubill on 2010-01-12
How can I identify my system's motherboard from the command line?

Thanks!

---

### Post by falconindy on 2010-01-12
dmidecode should do what you ask.

---

### Post by iponeverything on 2010-01-12
I don't think that there is a way to do it from the command line.

```
sudo lshw
```

will give you a lot of useful information..

Edit: Cool, just saw falconindy's post. I learned something new :)

---

### Post by seubill on 2010-01-12
```
dmidecode should do what you ask. 
```



That gave an amount of information about the CPU. memory, etc... but unfortunately could not id any motherboard info.

Can I get a hex string from the m.board somehow and then Google that?

---

### Post by falconindy on 2010-01-12
Look closer at dmidecode's output. Right near the top..

```
# dmidecode 2.10
SMBIOS 2.4 present.
38 structures occupying 1199 bytes.
Table at 0x000F0100.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Award Software International, Inc.
        Version: F1
        Release Date: 06/11/2008
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                5.25"/360 kB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
[B]        Manufacturer: Gigabyte Technology Co., Ltd.
        Product Name: EP45T-DS3R[/B]
        Version:  
        Serial Number:  
        UUID: 00000000-0000-0000-0000-001FD022BD0E
        Wake-up Type: Power Switch
        SKU Number:  
        Family:
```
That's definitely my motherboard in bold.

---

### Post by seubill on 2010-01-13
Falconindy, thankyou! I have it now.


```
Handle 0x0200, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Dell Inc.          
	Product Name: 0WG261
	Version:    
	Serial Number: ..CN698615AH1E50.

```


I was experiencing some weirdness in terminal last night, as every time I ran the "dmidecode" command, about ¼ of the top portion of the output was chopped off. This installation of Karmic has both the Ubuntu and Xubuntu desktops installed and under Applications>Accessories>Terminal, "Terminal" is listed twice. Only after I clicked onto the second "Terminal" selection today, did I get a full output. Weird.

Anyway, I Googled 0WG261 and found the motherboard that I'm needing. Thanks again.

---

