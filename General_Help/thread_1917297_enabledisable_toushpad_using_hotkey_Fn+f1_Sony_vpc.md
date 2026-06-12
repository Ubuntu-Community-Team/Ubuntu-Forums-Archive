---
title: "enable/disable toushpad using hotkey Fn+f1 Sony vpceh1s1e (not working)"
date: 2012-01-29
forum: General Help
---

### Post by KHALED-LELA on 2012-01-29
```
acpi_listen
```o/p
> 
sony/hotkey SNC 00000001 0000000c
sony/hotkey SNC 00000001 0000003b
```
xinput --list
```> 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; 2.4GHz 2way RF Receiver                     id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=15    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer             id=10    [slave  keyboard (3)]
    &#8627; 2.4GHz 2way RF Receiver                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
 after search i made >
1- put script /etc/acpi/sony-touchpad.sh
> sony-touchpad.sh```

#!/bin/sh
# toggle synaptic touchpad on/off
MOUSESTATE=$(xinput list-props "PS/2 Mouse" | grep Enabled | grep -Eo '.$')
if [ $MOUSESTATE = 0 ]; then xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 1
else xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 0; fi

```2-put event  /etc/acpi/event/sony-touchpad
```

event=sony/hotkey SNC 00000001 0000000c
action=/etc/acpi/sony-tochpad.sh

```3-restart acpi
```

sudo /etc/init.d/acpid restart

```4- nothing work  ](*,)
5- any one help me :KS

---

### Post by pbrane on 2012-01-29
If you're trying to enable/disable the touchpad you need to change the xinput set-int-prop device name.
```

#!/bin/sh
# toggle synaptic touchpad on/off
MOUSESTATE=$(xinput list-props "PS/2 Mouse" | grep Enabled | grep -Eo '.$')
if [ $MOUSESTATE = 0 ]; then xinput set-int-prop "**AlpsPS/2 ALPS GlidePoint**" "Device Enabled" 8 1
else xinput set-int-prop "**AlpsPS/2 ALPS GlidePoint**" "Device Enabled" 8 0; fi

```
Your version is trying to enable/disable the PS/2 mouse.

---

### Post by KHALED-LELA on 2012-01-29
> 
#!/bin/sh
# toggle synaptic touchpad on/off
MOUSESTATE=$(xinput list-props "PS/2 Mouse" | grep Enabled | grep -Eo '.$')
if [ $MOUSESTATE = 0 ]; then xinput set-int-prop "**AlpsPS/2 ALPS GlidePoint**" "Device Enabled" 8 1
else xinput set-int-prop "**AlpsPS/2 ALPS GlidePoint**" "Device Enabled" 8 0; fi

>  not work 

and i run my old script (PS/2 Mouse)
```
sudo /etc/acpi/sony-toushpad.sh
```
work good , but when use Fn+f1 not work why ?

---

