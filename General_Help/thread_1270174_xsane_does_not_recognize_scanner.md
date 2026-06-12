---
title: "xsane does not recognize scanner"
date: 2009-09-19
forum: General Help
---

### Post by hofstra14 on 2009-09-19
On Ubuntu 9.04 I have a CanoScan FB620P scanner connected via parallel port.  According to the xsane docs this is a supported device.  However when xsane loads it does not find any scanner present.

---

### Post by Bachstelze on 2009-09-19
Try running

```
sudo sane-find-scanner
```

---

### Post by jlathrop on 2009-09-23
I have been having the same problem with Jaunty not recognizing a CanoScan FB620P on parport0

sane find-scanner  replies:

 # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


The   CanoScan FB620P  is a parallel scanner!

I have removed the # from in front of the Canon_pp  line in etc/sane.d/dll.conf 

I have run Sane from sudo  which just hangs.  

I have power cycled the scanner

Before scanning with sane  dmesg | grep port  reported: 

[ 12.421607] parport_pc 00:0a: reported by Plug and Play ACPI
[   12.421699] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]


after scanning with sane   dmesg | grep port  reported: 

[   14.586501] lp0: using parport0 (interrupt-driven).
[ 1867.544066] parport0: FIFO is stuck
[ 1867.592141] parport0: PE,2 timeout (1) in ecp_write_block_pio
[ 1867.640086] parport0: BUSY timeout (1) in ecp_write_block_pio
[ 1893.212259] parport0: BUSY timeout (-4) in ecp_write_block_pio


sudo SANE_DEBUG_CANON_PP=255 scanimage -L   reports: 



[sanei_debug] Setting debug level of canon_pp to 255.
[canon_pp] >> sane_init(0xbfa27138, 0x804d5c0): sane-backends 1.0.19
[canon_pp] sane_init: >> ieee1284_find_ports
[canon_pp] sane_init: 0 << ieee1284_find_ports
[canon_pp] sane_init: 1 parallel port(s) found.
[canon_pp] sane_init: port parport0
[canon_pp] >> init_device
[canon_pp] init_device: [configuring options]
[canon_pp] init_device: configuring opt: num_options
[canon_pp] init_device: configuring opt: resolution
[canon_pp] init_device: configuring opt: colour mode
[canon_pp] init_device: configuring opt: bit depth
[canon_pp] init_device: configuring opt: tl-x
[canon_pp] init_device: configuring opt: tl-y
[canon_pp] init_device: configuring opt: br-x
[canon_pp] init_device: configuring opt: br-y
[canon_pp] init_device: configuring opt: calibrate
[canon_pp] init_device: done opts
[canon_pp] << init_device
[canon_pp] sane_init: ># Define which port to use if one isn't specified - you should only have<
[canon_pp] sane_init: ># one of these lines!<
[canon_pp] sane_init: ># This is the default port to be used - others will be detected<
[canon_pp] sane_init: >#  ieee1284<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >parport0<
[canon_pp] sane_init: Unknown configuration command![canon_pp] sane_init: ><
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Define the location of our pixel weight file, can begin with ~/ if needed.<
[canon_pp] sane_init: ># You can have as many of these as you like - lines with ports that don't exist<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># will be ignored.<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># Parameters are:<
[canon_pp] sane_init: ># calibrate /path/to/calibration-file port-name<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># The format of port-name is dependant on your OS version.<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># If a file isn't speficied, the default name will be<
[canon_pp] sane_init: ># ~/.sane/canon_pp-calibration-[port-name]<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >calibrate ~/.sane/canon_pp-calibration-pp0 parport0<
[canon_pp] sane_init: calibrate line, calibrate ~/.sane/canon_pp-calibration-pp0 parport0
[canon_pp] sane_init: Finding scanner on port 'parport0'
[canon_pp] sane_init: Found!
[canon_pp] sane_init: Parsed cal, for port 'parport0', weight file is '~/.sane/canon_pp-calibration-pp0'.
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># calibrate /etc/sane/my_calibration parport1<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Enable the next line if you're having trouble with ECP mode such as I/O<
[canon_pp] sane_init: ># errors.  Nibble mode is slower, but more reliable.<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >#force_nibble<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Set a default initialisation mode for each port.  Valid modes are:<
[canon_pp] sane_init: ># AUTO        (attempts to automatically detect by trying both methods)<
[canon_pp] sane_init: >FB620P    (10101010 style.. also works for FB320P)<
[canon_pp] sane_init: Unknown configuration command![canon_pp] sane_init: ># FB630P    (11001100 style.. also works for FB330P, N340P, N640P)<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >init_mode AUTO parport0<
[canon_pp] sane_init: Parsed init.
[canon_pp] sane_init: >init_mode FB620P parport0<
[canon_pp] sane_init: Parsed init.
[canon_pp] sane_init: ># init_mode FB630P parport0<
[canon_pp] detect_mode: Opening port parport0
[canon_pp] detect_mode: Claiming port.
[canon_pp] detect_mode: Port supports ECP-H.
[canon_pp] detect_mode: Port supports interrupts.
[canon_pp] detect_mode: Port supports DMA.
[canon_pp] detect_mode: Using ECP-H Mode
[canon_pp] sane_init: >> initialise
[canon_pp] WARNING: Don't know how to reset an FBx20P, you may have to power cycle
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1b
[canon_pp] Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1b
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1b
[canon_pp] Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1b
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1b
[canon_pp] Timeout: Reply 2 (0x0c in 0x1f) - Status = 0x1b
[canon_pp] initialise: could not wake scanner
[canon_pp] sane_init: << 1 initialise
[canon_pp] sane_init: Couldn't contact scanner on port parport0. Probably no scanner there?
[canon_pp] << sane_init
[canon_pp] >> sane_get_devices (0xbfa27198, 0)
[canon_pp] << sane_get_devices

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[canon_pp] >> sane_exit
[canon_pp] << sane_exit

This scanner works fine on this computer with winme! so it is not a hardware issue. 

Any suggestions?

Thanks in advance

Jon

---

### Post by CEB2nd on 2009-09-23
Does xsane find the scanner if you run it as root?
Open terminal and type "gksudo xsane" without the quotation
marks of course. If it recognizes it then you probably have
a problem with permissions.

---

### Post by jlathrop on 2009-09-24
Ok I got it to recognize the scanner by hash marking  the  ieee1284 line in Canon_pp.conf and power cycling every time before I try to do something with it. I also disconnected an old turned off printer from the parallel port.    Xsane comes up  listing the fb620p   and the scanner starts to scan but then hangs after a few seconds of scanning. 

Is there anything I can do to get this scanner to work properly under Ubuntu.

---

### Post by hbbliss on 2009-10-16
Xsane treats parallel scanners as belonging only to root. Running Xsane as just a user will not find the scanner. Running sudo chown -R :(your user name here) /dev/parport0 may fix the permission problem. Permissions for /.sane/xsane may also need to be changed. Hope this helps.

---

