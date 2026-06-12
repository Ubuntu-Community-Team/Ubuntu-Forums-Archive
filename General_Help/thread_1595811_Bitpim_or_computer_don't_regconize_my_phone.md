---
title: "Bitpim or computer don't regconize my phone"
date: 2010-10-13
forum: General Help
---

### Post by demonic_crow on 2010-10-13
How do I get Bitpim to work on my lg vu cu920 phone on Ubuntu 10.04? I have the data cable.   I seen serval  peoples said they got it to work but they never said how.  I set the  phone to the lg-vx8700.  Sometime I get ports that will be open and then  not.  It doesn't mount under the mass storage.  Would be awesome if  someone on here could explain how they did it.  Believe me I looked all  over google and the forums and they all talk about they got it to  work but no further details.  Can't really bring up really old threads  on here.  Thanks everyone, I'm really can't wait to finally be able to see my file system :D.

---

### Post by demonic_crow on 2010-10-13
Error i get in bitpim trying to connect to a port.

```
BitPim version: 1.0.6-Debian
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "/usr/share/bitpim/code/gui.py", line 284, in run
    res=call()
  File "/usr/share/bitpim/code/gui.py", line 159, in __call__
    return apply(self.method, self.args+args, d)
  File "/usr/share/bitpim/code/gui.py", line 2042, in fulldirlisting
    self.setupcomm()
  File "/usr/share/bitpim/code/gui.py", line 1866, in setupcomm
    configparameters=comcfg)
  File "/usr/share/bitpim/code/commport.py", line 68, in __init__
    self._openport(self.port, *self.params)
  File "/usr/share/bitpim/code/commport.py", line 97, in _openport
    self.ser=self._openusb(port, timeout)
  File "/usr/share/bitpim/code/commport.py", line 129, in _openusb
    return _usbdevicewrapper(iface.openbulk(), timeout)
  File "/usr/lib/bitpim/native/usb/usb.py", line 172, in openbulk
    raise USBException()
USBException: could not claim interface 2: Device or resource busy

Variables by last 8 frames, innermost last

Frame run in /usr/share/bitpim/code/gui.py at line 277
       resultcb =  <gui.Callback instance at 0xc22decc>
            res =  None
           self =  <WorkerThread(BitPim helper, started daemon -1242215568)>
           item =  (<gui.Request instance at 0xc22dc8c>, <gui.Callback instance at 0xc22decc>)
           call =  <gui.Request instance at 0xc22dc8c>
             ex =  USBException('could not claim interface 2: Device or resource busy',)
              e =  USBException('could not claim interface 2: Device or resource busy',)
          first =  0

Frame __call__ in /usr/share/bitpim/code/gui.py at line 159
           self =  <gui.Request instance at 0xc22dc8c>
           args =  ()
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame fulldirlisting in /usr/share/bitpim/code/gui.py at line 2042
           self =  <WorkerThread(BitPim helper, started daemon -1242215568)>

Frame setupcomm in /usr/share/bitpim/code/gui.py at line 1866
           name =  'usb::002::015::2'
           self =  <WorkerThread(BitPim helper, started daemon -1242215568)>
       autofunc =  None
         comcfg =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
          klass =  <class commport.CommConnection at 0x9863bcc>

Frame __init__ in /usr/share/bitpim/code/commport.py at line 68
           baud =  115200
   autolistargs =  (<module 'phones.com_lgvx8700' from '/usr/share/bitpim/code/phones/com_lgvx8700.
           self =  <commport.CommConnection instance at 0xa89fc4c>
   hardwareflow =  False
   autolistfunc =  None
        timeout =  3.0
      logtarget =  <WorkerThread(BitPim helper, started daemon -1242215568)>
configparameters =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
   softwareflow =  False
           port =  'usb::002::015::2'

Frame _openport in /usr/share/bitpim/code/commport.py at line 110
           baud =  115200
          dummy =  0
    description =  None
           self =  <commport.CommConnection instance at 0xa89fc4c>
   hardwareflow =  False
        timeout =  3.0
   softwareflow =  False
           port =  'usb::002::015::2'

Frame _openusb in /usr/share/bitpim/code/commport.py at line 129
          iface =  <native.usb.usb.USBInterface instance at 0xc27402c>
      wantedbus =  '002'
           name =  'usb::002::015::2'
            bus =  <native.usb.usb.USBBus instance at 0xa59fe2c>
           self =  <commport.CommConnection instance at 0xa89fc4c>
      wanteddev =  '015'
        timeout =  3.0
         device =  <native.usb.usb.USBDevice instance at 0xa59ff2c>
    wantediface =  2
              _ =  'usb'

Frame openbulk in /usr/lib/bitpim/native/usb/usb.py at line 172
         epinno =  None
        epoutno =  None
            res =  -16
           self =  <native.usb.usb.USBInterface instance at 0xc27402c>
           epin =  <native.usb.usb.USBEndpoint instance at 0xc2740ac>
              v =  1
          epout =  <native.usb.usb.USBEndpoint instance at 0xc2740cc>
             ep =  <native.usb.usb.USBEndpoint instance at 0xc2740cc>
          match =  <function <lambda> at 0xc27241c>

```

---

### Post by demonic_crow on 2010-10-14
So when I do use sudo to run bitpim it will show a port that says its my phone.  After I tried to do it, it give me the error above.  So I go back to the ports and refresh it and it show that its not possible to open.

---

### Post by demonic_crow on 2010-10-14
anyone have any ideas, i been searching everywhere.

---

### Post by cookdav on 2010-11-02
Just installed Bitpim (under latest Kubuntu).

It is almost ANCIENT, as Ubuntu's Bipim is 1.06, yet Bitpim 1.07 was
released almost a YEAR ago. :confused: ](*,)

Someone needs to upgrade the Ubuntu repo with Bitpim
1.0.7.  (The 1.0.6 doesn't even SEEM to support Bluetooth!?
Or, else the 1.0.6 docs are sloppy.)

Ref:
> bitpim:
  Installed: 1.0.6.dfsg.1-6
  Candidate: 1.0.6.dfsg.1-6
  Version table:
     1.0.6.dfsg.1-6 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Packages
        100 /var/lib/dpkg/status


Both MEPIS and sidux offer Bitpim 1.0.7, so why doesn't K/Ubuntu????

---

