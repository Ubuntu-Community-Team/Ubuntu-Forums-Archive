---
title: "Serial Port not Recognized"
date: 2009-12-03
forum: General Help
---

### Post by Leberyo on 2009-12-03
Hi, I've been using Ubuntu for the past two weeks and loving it.  The only thing is, is that we have a Java based business program that allows us to print to an older bar code printer.  The problem is that the program doesn't recognize any com ports on this machine.  I installed the com port on my motherboard via a Com port riser that it has.  Could anybody give me an idea or clue to get this working?  If I can't get this program working I have to go back to Windoze...

Thanks

---

### Post by StuartN on 2009-12-03
> **Leberyo said:**
> The problem is that the program doesn't recognize any com ports on this machine.  I installed the com port on my motherboard via a Com port riser that it has.

These ports are /dev/ttys0 and /dev/ttys1. Minicom or gtkterm or kermit will set them up. Setserial is a basic speed and mode setting command.

**lshw** will list your hardware, **lspci -nnv** is a verbose pci list.

---

### Post by Leberyo on 2009-12-03
Thx for the reply.  Downloaded gtkterm.  Tried setting it up and sending a break command to the printer but it doesn't do anything.  I tried setting the flow control to xonxoff and it returned input output errors in the terminal.

Is there a way I can tell whether my printer and serial port are being recognized?

---

### Post by StuartN on 2009-12-03
> **Leberyo said:**
> I tried setting the flow control to xonxoff and it returned input output errors in the terminal.

Sorry, that should have been /dev/ttyS0 or /dev/ttyS1 with a capital S. You can check the settings with **stty -F /dev/ttyS0 -a** which lists all settings on file after -F. You may have to **sudo stty** to change settings, and man stty for options. This will return a setting, or an input/output error if it is not attached to hardware. **lspci** should have listed a port if one is present, but I am not sure if it lists the associated /dev file.

(there is no serial on this laptop).

---

### Post by Leberyo on 2009-12-03
I downloaded minicom and setup the baud rate to 9600 8N1.  When I type sudo stty I get this;
speed 38400 baud; line = 0;
eol = M-^?; eol2 = M-^?; swtch = M-^?;
ixany iutf8
and
dmesg | grep ttyS
[    1.671773] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.671982] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

I have no idea what it means though...

---

### Post by StuartN on 2009-12-03
> **Leberyo said:**
> I downloaded minicom and setup the baud rate to 9600 8N1.  When I type sudo stty I get this;
speed 38400 baud; line = 0;
eol = M-^?; eol2 = M-^?; swtch = M-^?;
ixany iutf8
and
dmesg | grep ttyS
[    1.671773] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.671982] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

I have no idea what it means though...

Oh, the good old days! It is a 16550 serial UART chip on interrupt (irq) 4 using memory addressing at 0x3f8, which is of very little relevance to anything most people would do...

It is also at /dev/ttyS0, so using this file within gtkterm ought to work without errors. Also, **stty -F /dev/ttyS0 -a** will list the port's settings (I think it lists the terminal settings if no file is specified).

If the baud rates match, then a few carriage returns, line feeds or page feeds should make the printer do something audible.

---

### Post by Leberyo on 2009-12-03
> **StuartN said:**
> Oh, the good old days! It is a 16550 serial UART chip on interrupt (irq) 4 using memory addressing at 0x3f8, which is of very little relevance to anything most people would do...

It is also at /dev/ttyS0, so using this file within gtkterm ought to work without errors. Also, **stty -F /dev/ttyS0 -a** will list the port's settings (I think it lists the terminal settings if no file is specified).

If the baud rates match, then a few carriage returns, line feeds or page feeds should make the printer do something audible.

Extreme noob here.  Could you show me how to send a line feed or something to the printer?  I set the printer to use 9600baud 8N1.

Running the command; stty -F /dev/ttyS0 -a
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke

---

### Post by Leberyo on 2009-12-04
I just tried the same program in Windows and it recognizes the Com port correctly.  So it's not a matter of it not being correctly connected.  Any other idea would be really appreciated.  I don't want to give up on Linux but it's a matter of necessity to get this program running with this printer.

---

### Post by StuartN on 2009-12-04
> **Leberyo said:**
> Could you show me how to send a line feed or something to the printer?

The output shows that the hardware is recognized, because stty would give **stty: /dev/ttyS0: Input/output error** if there was no hardware assigned to /dev/ttyS0.

You can simply copy text or a file to the port using **echo "Hello" > /dev/ttyS0** or **cat file.txt > /dev/ttyS0**. Minicom should also have facilities to write straight out.

---

### Post by Leberyo on 2009-12-04
> **StuartN said:**
> The output shows that the hardware is recognized, because stty would give **stty: /dev/ttyS0: Input/output error** if there was no hardware assigned to /dev/ttyS0.

You can simply copy text or a file to the port using **echo "Hello" > /dev/ttyS0** or **cat file.txt > /dev/ttyS0**. Minicom should also have facilities to write straight out.

Neither command does anything....

---

### Post by StuartN on 2009-12-04
> **Leberyo said:**
> Neither command does anything....

Quite possibly you need root permissions to write to a device, so either get a root shell (sudo bash) or run the command as root, sudo echo "Test" > /dev/ttyS0. Both commands are inside a regular terminal (Applications->Accessories->Terminal).

Also, are you sure that this device doesn't have a driver already?

---

### Post by Leberyo on 2009-12-04
The sudo hadn't worked either.
Driver?  Well, this program writes to the printer without the need for a driver.

---

### Post by sdowney717 on 2009-12-04
i do believe, if you want to see ports open up /dev folder and they will be named there

---

### Post by Leberyo on 2009-12-04
So here is what I did.  I tried adding the printer via Adminstration>Printing, said CUPS was off, turned it on.  It didn't automatically recognize the printer so I manually added it but from the available models, my printer doesn't show up (its a Citoh S4, or Citizen CLP-6001, 6002 variant).  I added another Citoh printer and tried to print a test page and the printer beeped an error message...  I'm getting a little closer...

---

### Post by StuartN on 2009-12-04
> **Leberyo said:**
> So here is what I did.  I tried adding the printer via Adminstration>Printing, said CUPS was off, turned it on.  It didn't automatically recognize the printer so I manually added it but from the available models, my printer doesn't show up (its a Citoh S4, or Citizen CLP-6001, 6002 variant).  I added another Citoh printer and tried to print a test page and the printer beeped an error message...  I'm getting a little closer...

Which port / path did that write out to? It should be listed somewhere in the CUPS configuration pages.

Presumably if you use the same path in your barcoding application, then it should write to the printer (although you might need to change permission on the path or run the application as root).

---

### Post by Leberyo on 2009-12-04
Well I selected serial port from the list of options.  My printer wasn't available so I later deleted the printer.

I tried something else that I found on another website and created a ttyS0.conf file in /etc/init (copied over the settings) and then sudo start ttyS0 which made my printer return an error message, so at least it sent something out...  It feels like Linux isn't initializing the Com port.  On windows this app automatically recognizes the Com port and I'm able to start using it.

---

### Post by StuartN on 2009-12-04
> **Leberyo said:**
> It feels like Linux isn't initializing the Com port.  On windows this app automatically recognizes the Com port and I'm able to start using it.

Linux is certainly initializing the port and assigning a path to it, and allowing you to set communication parameters. The problems are 1) you have no driver for this printer, and the manufacturer has no Linux drivers, and 2) your application needs to be configured with the path.

I do not know if there are any generic settings for Java or specific settings for your application. Many applications have a hidden text file called .application_name in your home directory. You can view hidden files with ls -a in the terminal or View->Hidden in Nautilus.

Edit: I just went and tried this on a beastie with a serial port. In a standard installation of Ubuntu 9.04, /dev/ttyS0 is the first serial port and is writeable by the user. **echo "test" > /dev/ttyS0** or **cat test.txt > /dev/ttyS0** send output to the port. CUPS recognizes the port and offers Serial#1 with the URI "serial:/dev/ttyS0?baud 19200".

The rest is up to a driver or application to create a meaningful stream for the device.

---

