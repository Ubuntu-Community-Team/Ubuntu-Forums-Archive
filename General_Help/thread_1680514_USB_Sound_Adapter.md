---
title: "USB Sound Adapter"
date: 2011-02-02
forum: General Help
---

### Post by viktorzk on 2011-02-02
Hello,

I cannot make my USB sound adapter the output device.

My laptop has a built-in sound card, which works fine. (But I do need a USB adapter sometimes, for irrelevant reasons.)

The USB adapter is: [http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=290366278243](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=290366278243)

When I plug it in (with headphones plugged into it), it makes some cracking noises in the headphones during initialization (read: while its LED is flashing), then the LED goes off and the headphones are silent.

I am using Ubuntu Lucid 32-bit, ALSA version 1.0.21.

```

***:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4700000 irq 16
 1 [Set            ]: USB-Audio - USB Headphone Set
                      USB Headphone Set at usb-0000:00:1d.2-1, full speed

``````

***:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 006: ID 0c76:1607 JMTek, LLC. 
.... (4 more root hubs and a fingerprint sensor)

```The USB adapter is "JMTek, LLC".


```

***:~$ lsusb -v
.... other devices

Bus 004 Device 006: ID 0c76:1607 JMTek, LLC. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0c76 JMTek, LLC.
  idProduct          0x1607 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          247
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength          100
        bInCollection           2
        baInterfaceNr( 0)       1
        baInterfaceNr( 1)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0001
          Left Front (L)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            17
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID              49
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            18
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          2
        bSourceID              33
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      5 (SELECTOR_UNIT)
        bUnitID                33
        bNrInPins               1
        baSource( 0)           50
        iSelector               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                49
        bSourceID              65
        bControlSize            1
        bmaControls( 0)      0x01
          Mute
        bmaControls( 1)      0x02
          Volume
        bmaControls( 2)      0x02
          Volume
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                50
        bSourceID               2
        bControlSize            1
        bmaControls( 0)      0x43
          Mute
          Volume
          Automatic Gain
        bmaControls( 1)      0x00
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                51
        bSourceID               2
        bControlSize            1
        bmaControls( 0)      0x03
          Mute
          Volume
        bmaControls( 1)      0x00
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      4 (MIXER_UNIT)
        bUnitID                65
        bNrInPins               2
        baSourceID( 0)          1
        baSourceID( 1)         51
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        bmControls         0x00
        iMixer                  0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x00c8  1x 200 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         1 Milliseconds
          wLockDelay              1 Milliseconds
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink          18
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0064  1x 100 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               8

--- other devices

```

```

***:~$ cat /usr/share/alsa/alsa.conf
#
#  ALSA library configuration file
#

# pre-load the configuration files

@hooks [
    {
        func load
        files [
            "/usr/share/alsa/pulse.conf"
            "/usr/share/alsa/bluetooth.conf"
            "/etc/asound.conf"
            "~/.asoundrc"
        ]
        errors false
    }
]

# load card-specific configuration files (on request)

cards.@hooks [
    {
        func load
        files [
            {
                @func concat
                strings [
                    { @func datadir }
                    "/cards/aliases.conf"
                ]
            }
        ]
    }
    {
        func load_for_all_cards
        files [
            {
                @func concat
                strings [
                    { @func datadir }
                    "/cards/"
                    { @func private_string }
                    ".conf"
                ]
            }
        ]
        errors false
    }
]

#
# defaults
#

# show all name hints also for definitions without hint {} section
defaults.namehint.showall off
# show just basic name hints
defaults.namehint.basic on
# show extended name hints
defaults.namehint.extended off
#
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
# truncate files via file or tee PCM
defaults.pcm.file_format    "raw"
defaults.pcm.file_truncate    true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

#
#  PCM interface
#

# redirect to load-on-demand extended pcm definitions
pcm.cards cards.pcm

pcm.default cards.pcm.default
pcm.front cards.pcm.front
pcm.rear cards.pcm.rear
pcm.center_lfe cards.pcm.center_lfe
pcm.side cards.pcm.side
pcm.surround40 cards.pcm.surround40
pcm.surround41 cards.pcm.surround41
pcm.surround50 cards.pcm.surround50
pcm.surround51 cards.pcm.surround51
pcm.surround71 cards.pcm.surround71
pcm.iec958 cards.pcm.iec958
pcm.spdif iec958
pcm.hdmi cards.pcm.hdmi
pcm.dmix cards.pcm.dmix
pcm.dsnoop cards.pcm.dsnoop
pcm.modem cards.pcm.modem
pcm.phoneline cards.pcm.phoneline

pcm.hw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
        }
    }        
    type hw
    card $CARD
    device $DEV
    subdevice $SUBDEV
    hint {
        show {
            @func refer
            name defaults.namehint.extended
        }
        description "Direct hardware device without any conversions"
    }
}

pcm.plughw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
        }
    }        
    type plug
    slave.pcm {
        type hw
        card $CARD
        device $DEV
        subdevice $SUBDEV
    }
    hint {
        show {
            @func refer
            name defaults.namehint.extended
        }
        description "Hardware device with all software conversions"
    }
}

pcm.plug {
    @args [ SLAVE ]
    @args.SLAVE {
        type string
    }
    type plug
    slave.pcm $SLAVE
}

pcm.shm {
    @args [ SOCKET PCM ]
    @args.SOCKET {
        type string
    }
    @args.PCM {
        type string
    }
    type shm
    server $SOCKET
    pcm $PCM
}

pcm.tee {
    @args [ SLAVE FILE FORMAT ]
    @args.SLAVE {
        type string
    }
    @args.FILE {
        type string
    }
    @args.FORMAT {
        type string
        default {
            @func refer
            name defaults.pcm.file_format
        }
    }
    type file
    slave.pcm $SLAVE
    file $FILE
    format $FORMAT
    truncate {
        @func refer
        name defaults.pcm.file_truncate
    }
}

pcm.file {
    @args [ FILE FORMAT ]
    @args.FILE {
        type string
    }
    @args.FORMAT {
        type string
        default {
            @func refer
            name defaults.pcm.file_format
        }
    }
    type file
    slave.pcm null
    file $FILE
    format $FORMAT
    truncate {
        @func refer
        name defaults.pcm.file_truncate
    }
}

pcm.null {
    type null
    hint {
        show {
            @func refer
            name defaults.namehint.basic
        }
        description "Discard all samples (playback) or generate zero samples (capture)"
    }
}

#
#  Control interface
#
    
ctl.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_CTL_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.ctl.card
        }
    }
}

ctl.hw {
    @args [ CARD ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_CTL_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.ctl.card
            }
        }
    }
    type hw
    card $CARD
}

ctl.shm {
    @args [ SOCKET CTL ]
    @args.SOCKET {
        type string
    }
    @args.CTL {
        type string
    }
    type shm
    server $SOCKET
    ctl $CTL
}

#
#  RawMidi interface
#

rawmidi.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_RAWMIDI_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.rawmidi.card
        }
    }
    device {
        @func igetenv
        vars [
            ALSA_RAWMIDI_DEVICE
        ]
        default {
            @func refer
            name defaults.rawmidi.device
        }
    }
}

rawmidi.hw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_RAWMIDI_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.rawmidi.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_RAWMIDI_DEVICE
            ]
            default {
                @func refer
                name defaults.rawmidi.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default -1
    }
    type hw
    card $CARD
    device $DEV
    subdevice $SUBDEV
    hint {
        description "Direct rawmidi driver device"
        device $DEV
    }
}

rawmidi.virtual {
    @args [ MERGE ]
    @args.MERGE {
        type string
        default 1
    }
    type virtual
    merge $MERGE
}

#
#  Sequencer interface
#

seq.default {
    type hw
}

seq.hw {
    type hw
}

#
#  HwDep interface
#

hwdep.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_HWDEP_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.hwdep.card
        }
    }
    device {
        @func igetenv
        vars [
            ALSA_HWDEP_DEVICE
        ]
        default {
            @func refer
            name defaults.hwdep.device
        }
    }
}

hwdep.hw {
    @args [ CARD DEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_HWDEP_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.hwdep.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_HWDEP_DEVICE
            ]
            default {
                @func refer
                name defaults.hwdep.device
            }
        }
    }
    type hw
    card $CARD
    device $DEV
}

#
#  Timer interface
#

timer_query.default {
    type hw
}

timer_query.hw {
    type hw
}

timer.default {
    type hw
    class {
        @func refer
        name defaults.timer.class
    }
    sclass {
        @func refer
        name defaults.timer.sclass
    }
    card {
        @func refer
        name defaults.timer.card
    }
    device {
        @func refer
        name defaults.timer.device
    }
    subdevice {
        @func refer
        name defaults.timer.subdevice
    }
    hint.description "Default direct hardware timer device"
}

timer.hw {
    @args [ CLASS SCLASS CARD DEV SUBDEV ]
    @args.CLASS {
        type integer
        default {
            @func refer
            name defaults.timer.class
        }
    }
    @args.SCLASS {
        type integer
        default {
            @func refer
            name defaults.timer.sclass
        }
    }
    @args.CARD {
        type string
        default {
            @func refer
            name defaults.timer.card
        }
    }
    @args.DEV {
        type integer
        default {
            @func refer
            name defaults.timer.device
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.timer.subdevice
        }
    }
    type hw
    class $CLASS
    sclass $SCLASS
    card $CARD
    device $DEV
    subdevice $SUBDEV
}

```

I tried editing /usr/share/alsa/alsa.conf (replaced the 0 with 1 in "defaults.ctl.card 0" and "defaults.pcm.card 0"), then running "sudo alsa force-reload" and "sudo alsa-utils restart". The former resulted in noice coming through the headphones while alsa was reloading (both with the unedited and with the edited alsa.conf).


Thanks!

---

### Post by viktorzk on 2011-02-03
bump

---

### Post by viktorzk on 2011-02-04
bump

---

### Post by libertyspike138 on 2011-05-04
Anyone ever find a solution to this problem? I have the same usb sound card with no onboard sound or open slots so I'm running 11.04 without sound but need it.

---

