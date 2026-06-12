---
title: "Wammu and gnome phone manager problem"
date: 2010-04-14
forum: General Help
---

### Post by coldraven on 2010-04-14
I have been trying to backup my Nokia 5140 phone. I just bought a CA-42 cable which works in Windows but not in Ubuntu.
After looking at the output from dmesg I have been trying port /dev/ttyUSB0 but without luck. What am I doing wrong?

[29351.260062] usb 6-2: new full speed USB device using ohci_hcd and address 2
[29351.451355] usb 6-2: configuration #1 chosen from 1 choice
[29351.482202] usbcore: registered new interface driver usbserial
[29351.482247] USB Serial support registered for generic
[29351.482381] usbcore: registered new interface driver usbserial_generic
[29351.482388] usbserial: USB Serial Driver core
[29351.487711] USB Serial support registered for pl2303
[29351.487780] pl2303 6-2:1.0: pl2303 converter detected
[29351.509290] usb 6-2: pl2303 converter now attached to ttyUSB0
[29351.509330] usbcore: registered new interface driver pl2303
[29351.509336] pl2303: Prolific PL2303 USB to serial adaptor driver

It looks to me that the Prolific serial to USB adapter is being detected OK at ttyUSB0 but it won't connect.

Update: I installed gammu, ran gammu-config and finally got a connection.
Wammu is too buggy to use and gnome phone manager does not work at all!

---

### Post by TaimurK on 2010-07-09
I cant even see my usb to serial cable or my webcam on my Vaio Laptop FZ150E
:(

---

### Post by labinnsw on 2010-07-17
Was this solved?!!! How?

OK. I see it.

---

### Post by serg_stetsuk on 2011-02-22
I found that my Nokia 6610 with CA-42 needs to be initialized before using as a modem with AT-commands from console. So I sniffed Nokia Windows Connection Protocol and tried to write simple perl script which performs such an initialization:

  use Device::Gsm;

### First start only for initialization of usb-serial converter and NOKIA phone
### for accepting AT-commands
  my $gsm = new Device::Gsm( port => '/dev/ttyUSB0');
  $gsm->connect(baudrate => 19200);
  $gsm->port()->purge_all;

  $output_string=pack('H*','617426660d00'); #send at&f
  $count_out = $gsm->port()->write($output_string);

  sleep(1);

  $output_string=pack('H*','61742A6E6F6B6961666275730D0A00'); #at*nokiafbus
  $count_out = $gsm->port()->write($output_string);

  sleep(1);

  $gsm->port()->purge_all;
  
  $gsm->port()->baudrate(115200);
  $gsm->port()->write_settings;

  $gsm->port()->purge_all;

  $output_string=pack('H*','1E0010DA00060001000001600FBD');    #unknown command 1
  $count_out = $gsm->port()->write($output_string);

  sleep(1);
  $output_string=pack('H*','1E0010D7000800010012040001410B8D');    #unknown command 1
  $count_out = $gsm->port()->write($output_string);

  sleep(1);
  
  $InBytes = 4;
  ($count_in, $string_in) = $gsm->port()->read($InBytes);    #here we have to read 4 bytes
  
  sleep(1);
  
  $gsm->port()->purge_all;
    undef $gsm;
##After this initialization you can open port with any terminal

##Let's make some work with sms
###########################################################################
  my $gsm = new Device::Gsm( port => '/dev/ttyUSB0');
  $gsm->connect(baudrate => 115200);
  # Send quickly a short text message
#  $gsm->send_sms(
#      recipient => '+380502222222',
#      content   => 'Hello world! from Device::Gsm'
#  );

  # Get list of Device::Gsm::Sms message objects
    for( $gsm->messages('SM') )
    {
        print $_->sender(), '>> ', $_->content(), "\n";
    }
  # Delete message #1
    #~ $gsm->delete_sms(1, 'SM');
    undef $gsm;

It works for me even after Nokia power restart. You can use this method without any gammu/wammu.

---

