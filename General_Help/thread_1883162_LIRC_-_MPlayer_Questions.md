---
title: "LIRC - MPlayer Questions"
date: 2011-11-18
forum: General Help
---

### Post by Akovia on 2011-11-18
Can't seem to get LIRC to play nice with mplayer and am finally out of ideas. Been on this 2 solid days and I think I'm running in circles now.

Xubuntu 10.04 (Lucid) 2.6.32-35-generic SMP i686
lircd 0.8.6
MPlayer SVN-r34349-4.4.3
Prolific Technology, Inc. PL2303 Serial Port (USB > RS232)
Home Electro - IRA3 (IRMAN Clone)

More specifically I'm really trying to control UMPlayer (for starters) but I realize this is just a front-end for mplayer. The real rub here is that I don't get any response from either mplayer or totem via LIRC, but both UMPlayer and SMPlayer will respond to *most* of the commands I send, but others get no response at all. 

Play, fullscreen, next & previous, all fail, but most everything else seems to work. I have fine tuned my remote (Sony RMT-D223A) via irrecord and verified all the buttons I am using with irw, so I know my key presses are being acknowledged. I just don't know how to drill this down any further, including why I can't get any response from either Totem or mplayer directly. Do these packages need to be reconfigured, and if so why does UMPlayer and SMPlayer have any functionality at all if they are just front-ends for mplayer?

I was also curious if I could use irxevent as a work around to send key strokes instead of built-in commands. Seems like a hack to me and of course more overhead so I'm trying not to spend any time on it unless a solution doesn't present itself otherwise.

Here are some of the relevant configuration entries.

```
#FAIL
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_PLAY
    config = play
end
begin
     remote = RMT-D223A
     prog = mplayer
     button = KEY_PAUSE
     config = osd\nosd\npause
     config = pasue\nosd\nosd
     repeat = 0
     delay = 0
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_STOP
    config = stop
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_T
    config = frame_step
end
# FAIL
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_FORWARD
    config = pt_step 1
    repeat = 3
end
# FAIL
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_BACK
    config = pt_step -1
    repeat = 3
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_NEXT
    config = seek_chapter 1
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_PREVIOUS
    config = seek_chapter -1
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_VOLUMEUP
    config = volume 3
    repeat = 1
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_VOLUMEDOWN
    config = volume -3
    repeat = 1
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_SUBTITLE
    config = vobsub_lang
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_AUDIO
    config = switch_audio
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_KPPLUS
    config = seek 5
    repeat = 1
end
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_KPMINUS
    config = seek -5
    repeat = 1
end
#FAIL
begin
    prog = mplayer
    remote = RMT-D223A
    button = KEY_INFO
    config = vo_fullscreen
end
```

```
begin remote

  name  RMT-D223A
  bits           48
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0xFFFF
  gap          85736
  toggle_bit_mask 0x2220A82EB28

      begin codes
          KEY_DOWN                 0xFFC36473623C
          KEY_UP                   0xFFC3754F6D3C
          KEY_LEFT                 0xFFC374436E3C
          KEY_RIGHT                0xFFC355BC613C
          KEY_ENTER                0xFF3F8B4C6E3C
          KEY_1                    0xFF3F5940613C
          KEY_2                    0xFF3F49706D3C
          KEY_3                    0xFF3F584C623C
          KEY_4                    0xFF3F487C6E3C
          KEY_5                    0xFF3F6983613C
          KEY_6                    0xFF3F79B36D3C
          KEY_7                    0xFF3F688F623C
          KEY_8                    0xFF3F78BF6E3C
          KEY_9                    0xFF3F9A70613C
          KEY_0                    0xFF3F8A406D3C
          KEY_AUDIO                0xFF03A680613C
          KEY_SUBTITLE             0xFF03877F6E3C
          KEY_ESC                  0xFF3FABBF623C
          KEY_INFO                 0xFFF39A8F613C
          KEY_MENU                 0xFFFFBB406E3C
          KEY_VOLUMEUP             0xFF3C54000000
          KEY_VOLUMEDOWN           0xFF3C44000000
          KEY_CHANNELUP            0xFFFF78706E3C
          KEY_CHANNELDOWN          0xFFFF598F613C
          KEY_VIDEO                0xFFCC75000000
          KEY_TEXT                 0xFF0F9673613C
          KEY_SELECT               0xFFFF6840623C
          KEY_CLEAR                0xFF3FBB8F6E3C
          KEY_CLOSE                0xFFFF5883623C
          Key_Directory            0xFFFFAB70623C
          Key_Title                0x2E0460078250
          Key_Time                 0xCCF39ABF51F0
          KEY_S                    0xFF3FBA836D3C
          KEY_TV                   0xCFC45CE05FE7
          KEY_Setup                0xFFF3BB706E3C
          KEY_T                    0xCCF348B35EF0
          KEY_Previous             0xFFCF654F613C
          KEY_Next                 0xFFCF757F6D3C
          KEY_Play                 0xFFCF6443623C
          Key_Pause                0xFFCFB64F6D3C
          KEY_Stop                 0xFFCFA67F613C
          Key_Zoom                 0xCCCF754F5DF0
          KEY_Forward              0xFFCF558C613C
          KEY_Back                 0xFFCF74736E3C
          KEY_KPMinus              0xFFF359BF613C
          KEY_KPPlus               0xCCF3598F51F0
      end codes

end remote
```

```
$ irw
ffffffcf6443623c 00 KEY_Play RMT-D223A
ffffffcfb64f6d3c 00 Key_Pause RMT-D223A
ffffffcfa67f613c 00 KEY_Stop RMT-D223A
ffffcccf754f5df0 00 Key_Zoom RMT-D223A
ffffffcf558c613c 00 KEY_Forward RMT-D223A
ffffffcf74736e3c 00 KEY_Back RMT-D223A
ffffccf3598f51f0 00 KEY_KPPlus RMT-D223A
fffffff359bf613c 00 KEY_KPMinus RMT-D223A
ffffffcf654f613c 00 KEY_Previous RMT-D223A
ffffffcf757f6d3c 00 KEY_Next RMT-D223A
ffffccf348b35ef0 00 KEY_T RMT-D223A
ffffff3fabbf623c 00 KEY_ESC RMT-D223A
ffffff03a680613c 00 KEY_AUDIO RMT-D223A
ffffff03877f6e3c 00 KEY_SUBTITLE RMT-D223A
ffffff3c54000000 00 KEY_VOLUMEUP RMT-D223A
ffffff3c44000000 00 KEY_VOLUMEDOWN RMT-D223A
fffffff39a8f613c 00 KEY_INFO RMT-D223A

```

Thanks for any help,
Ako

---

