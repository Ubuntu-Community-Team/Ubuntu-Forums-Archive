---
title: "Perl problem"
date: 2012-08-21
forum: General Help
---

### Post by j666gak on 2012-08-21
Hello,

I have found a very useful script when I get it working, it was posted a few years ago. It will pull information off my blood testing meter. However when trying to run the script I keep getting the following error, please can somebody help?

```
Can't call method "user_msg" on an undefined value at meter.pl line 11.
```

This is the script
```
#!/usr/bin/perl -w

use strict;

use Device::SerialPort qw( :PARAM :STAT 0.07 );

my $PortObj = new Device::SerialPort ("/dev/tty0", 1);

$| = 1;

$PortObj->user_msg(1);
$PortObj->handshake('none');
$PortObj->baudrate(9600);
#$PortObj->baudrate(19200);
$PortObj->parity("none");
$PortObj->stopbits(1);
$PortObj->write_settings || undef $PortObj;

my $fnum = 0;
my $fdelim;
my $rdelim;
my $cdelim;
my $edelim;
my $control = 0;

my $count;
my $saw;

do {
	($count, $saw) = $PortObj->read(1);
	sleep 1 if ($count <= 0);
} while ($count <= 0 || $saw ne chr(5));

my $count_out = $PortObj->write(chr(6));
my $buf;
my $ncount = 0;

do {
	$buf = '';

	do {
		($count, $saw) = $PortObj->read(1);
		$buf .= $saw if ($count > 0);
	} while ($count <= 0 || $saw ne "\n");

	my $data = &validate_line($buf);

	if (!defined($data)) {
		$count_out = $PortObj->write(chr(21));
		$ncount++;

		die "Failed communications.\n" if ($ncount >= 6);
	}
	else {
		$ncount = 0;
		$count_out = $PortObj->write(chr(4));
	}

	#print "$data\n";
	&parse_data($data);
} while ($buf !~ /\x03/);

sub validate_line {
	my $line = shift;
	my $chk;

	if ($line !~ (/^\x02(\d)(.*)\r([\x03\x17])([0-98A-F]{2})\r/)) {
		warn "Bad line. Did not match expected format.\n";
		return undef;
	}

	my $frame = $1;
	my $text = $2;
	my $ftype = $3;
	my $refchk = $4;

	my $next = ($fnum + 1)%8;

	if ($frame != $fnum && $frame != $next) {
		warn "Bad frame. Expected $fnum or $next, got $frame\n";
		return undef;
	}

	$fnum = $frame;

	for (my $i = 0; substr($line, $i, 1) !~ /[\x03\x17]/; $i++) {
		my $c = substr($line, $i, 1);

		if ($c eq "\x02") {
			$chk = 0;
		}
		else {
			$chk += ord($c);
			$chk &=0xff;
		}

	}

	$chk += ord($ftype);
	$chk &=0xff;
	$chk = sprintf("%02X", $chk);

	if ($chk ne $refchk) {
		warn "Bad checksum. Got $chk, needed $refchk\n";
		return undef;
	}

	return $text;
}

sub parse_data {
	my $data = shift;
	my $dtype = substr($data, 0, 1);


	if ($dtype eq 'R') {
		my @fields = split(/$fdelim/, $data);
		my $snum = $fields[1];
		my $id = $fields[2];
		my $mes = $fields[3];
		my $unit = $fields[4];
		my $flag = $fields[6];
		my $mark = $fields[7];
		my $stat = $fields[8];
		my $dstamp = $fields[11];
		$dstamp = '000000000000' if (!defined($dstamp));
		my $date = substr($dstamp, 4, 2) . '/'
			. substr($dstamp, 6, 2) . '/'
			. substr($dstamp, 0, 4);
		my $time = substr($dstamp, 8, 2) . ':' . substr($dstamp, 10, 2);

		@fields = split(/$cdelim/, $id);
		$id = $fields[3];
		@fields = split(/$cdelim/, $unit);
		$unit = $fields[0];
		my $ref = $fields[1];

		print "$snum,$id,$mes,$unit,$ref,$flag,$mark,$stat,$date,$time\n"
			if (!$control && $id eq 'Glucose');
	}
	elsif ($dtype eq 'O') {
		my @fields = split(/$fdelim/, $data);
		my $snum = $fields[1];

		if (@fields >= 12 && $fields[11] eq 'Q') {
			$control = 1;
		}
		else {
			$control = 0;
		}

	}
	elsif ($dtype eq 'H') {
		$fdelim = '\\' . substr($data, 1, 1);
		$rdelim = '\\' . substr($data, 2, 1);
		$cdelim = '\\' . substr($data, 3, 1);
		$edelim = '\\' . substr($data, 4, 1);
		my @fields = split(/$fdelim/, $data);
		my $passwd = $fields[3];
		my $id = $fields[4];
		my $pid = $fields[11];
		my $ver = $fields[12];
		my $date = $fields[13];
		@fields = split(/$cdelim/, $id);
		my $pcode = $fields[0];
		my $sver = $fields[1];
		my $sn = $fields[2];

		print STDERR "Meter results from $date\n";
		print STDERR " Meter: $pcode (SN $sn) software version $sver\n";
	}
	# Skipping any other record types.

}

```

Perl 5 = installed
CPAN (Device:SerialPort) = installed
Platform = VM on VirtualBox


I am new to Linux, so i'm sorry if i'm missing something



Many Thanks
Guy

---

### Post by spjackson on 2012-08-22
$PortObj is undefined because the serial port package failed to open  "/dev/tty0".

Is tty0 the right device? If it is the right device, then you can give read/write permissions to everybody using:
```

sudo chmod o+rw /dev/tty0

```Is it a real serial port? I think these are normally ttyS0, ttyS1 etc. I don't know whether running it through a VM makes any difference.

---

### Post by j666gak on 2012-08-22
> **spjackson said:**
> $PortObj is undefined because the serial port package failed to open  "/dev/tty0".

Is tty0 the right device? If it is the right device, then you can give read/write permissions to everybody using:
```

sudo chmod o+rw /dev/tty0

```Is it a real serial port? I think these are normally ttyS0, ttyS1 etc. I don't know whether running it through a VM makes any difference.

I'm not sure which port it is on? From the information below I have point the script to /dev/sdb and then /dev/sdc, but still no joy

```
[guy@fedora17 Downloads]$ sudo tail -f /var/log/messages 
[sudo] password for guy:  
Aug 23 00:30:52 fedora17 kernel: [ 3828.268050] FAT-fs (sdc): Directory bread(block 526) failed 
Aug 23 00:30:52 fedora17 kernel: [ 3828.268050] FAT-fs (sdc): Directory bread(block 527) failed 
Aug 23 00:30:52 fedora17 udisksd[1181]: Cleaning up mount point /run/media/guy/GLUCOFACTS (device 8:32 no longer exist) 
Aug 23 00:31:37 fedora17 dbus-daemon[559]: dbus[559]: [system] Activating service name='net.reactivated.Fprint' (using servicehelper) 
Aug 23 00:31:37 fedora17 dbus[559]: [system] Activating service name='net.reactivated.Fprint' (using servicehelper) 
Aug 23 00:31:37 fedora17 dbus-daemon[559]: Launching FprintObject 
Aug 23 00:31:37 fedora17 dbus-daemon[559]: dbus[559]: [system] Successfully activated service 'net.reactivated.Fprint' 
Aug 23 00:31:37 fedora17 dbus[559]: [system] Successfully activated service 'net.reactivated.Fprint' 
Aug 23 00:31:37 fedora17 dbus-daemon[559]: ** Message: D-Bus service launched with name: net.reactivated.Fprint 
Aug 23 00:31:37 fedora17 dbus-daemon[559]: ** Message: entering main loop 
Aug 23 00:32:07 fedora17 dbus-daemon[559]: ** Message: No devices in use, exit 
Aug 23 00:32:36 fedora17 kernel: [ 3931.536522] usb 1-2: new full-speed USB device number 7 using ohci_hcd 
Aug 23 00:32:36 fedora17 kernel: [ 3931.970502] usb 1-2: New USB device found, idVendor=1a79, idProduct=6002 
Aug 23 00:32:36 fedora17 kernel: [ 3931.970513] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
Aug 23 00:32:36 fedora17 kernel: [ 3931.970521] usb 1-2: Product: Contour USB 
Aug 23 00:32:36 fedora17 kernel: [ 3931.970526] usb 1-2: Manufacturer: Bayer HealthCare LLC 
Aug 23 00:32:36 fedora17 kernel: [ 3931.970531] usb 1-2: SerialNumber: 0000000002116752 
Aug 23 00:32:36 fedora17 kernel: [ 3931.996666] generic-usb 0003:1A79:6002.0005: hiddev0,hidraw1: USB HID v10.10 Device [Bayer HealthCare LLC Contour USB] on usb-0000:00:06.0-2/input0 
Aug 23 00:32:36 fedora17 kernel: [ 3932.010527] scsi6 : usb-storage 1-2:1.1 
Aug 23 00:32:36 fedora17 mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:06.0/usb1/1-2" 
Aug 23 00:32:36 fedora17 mtp-probe: bus: 1, device: 7 was not an MTP device 
Aug 23 00:32:37 fedora17 kernel: [ 3933.034163] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 
Aug 23 00:32:37 fedora17 kernel: [ 3933.043509] scsi 6:0:0:1: Direct-Access                                    PQ: 0 ANSI: 2 
Aug 23 00:32:37 fedora17 kernel: [ 3933.058246] sd 6:0:0:0: Attached scsi generic sg2 type 0 
Aug 23 00:32:37 fedora17 kernel: [ 3933.060426] sd 6:0:0:1: Attached scsi generic sg3 type 0 
Aug 23 00:32:37 fedora17 kernel: [ 3933.245205] sd 6:0:0:0: [sdb] 930240 512-byte logical blocks: (476 MB/454 MiB) 
Aug 23 00:32:37 fedora17 kernel: [ 3933.254198] sd 6:0:0:1: [sdc] 1000000 512-byte logical blocks: (512 MB/488 MiB) 
Aug 23 00:32:37 fedora17 kernel: [ 3933.268180] sd 6:0:0:0: [sdb] Write Protect is off 
Aug 23 00:32:37 fedora17 kernel: [ 3933.282191] sd 6:0:0:1: [sdc] Write Protect is off 
Aug 23 00:32:37 fedora17 kernel: [ 3933.296179] sd 6:0:0:0: [sdb] No Caching mode page present 
Aug 23 00:32:37 fedora17 kernel: [ 3933.296186] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
Aug 23 00:32:37 fedora17 kernel: [ 3933.310205] sd 6:0:0:1: [sdc] No Caching mode page present 
Aug 23 00:32:37 fedora17 kernel: [ 3933.310211] sd 6:0:0:1: [sdc] Assuming drive cache: write through 
Aug 23 00:32:38 fedora17 kernel: [ 3933.406179] sd 6:0:0:0: [sdb] No Caching mode page present 
Aug 23 00:32:38 fedora17 kernel: [ 3933.406186] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
Aug 23 00:32:38 fedora17 kernel: [ 3933.420230] sd 6:0:0:1: [sdc] No Caching mode page present 
Aug 23 00:32:38 fedora17 kernel: [ 3933.420237] sd 6:0:0:1: [sdc] Assuming drive cache: write through 
Aug 23 00:32:38 fedora17 kernel: [ 3933.448220]  sdb: 
Aug 23 00:32:38 fedora17 kernel: [ 3933.474609]  sdc: 
Aug 23 00:32:38 fedora17 kernel: [ 3933.562300] sd 6:0:0:0: [sdb] No Caching mode page present 
Aug 23 00:32:38 fedora17 kernel: [ 3933.562306] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
Aug 23 00:32:38 fedora17 kernel: [ 3933.562310] sd 6:0:0:0: [sdb] Attached SCSI removable disk 
Aug 23 00:32:38 fedora17 kernel: [ 3933.609102] sd 6:0:0:1: [sdc] No Caching mode page present 
Aug 23 00:32:38 fedora17 kernel: [ 3933.609108] sd 6:0:0:1: [sdc] Assuming drive cache: write through 
Aug 23 00:32:38 fedora17 kernel: [ 3933.609112] sd 6:0:0:1: [sdc] Attached SCSI removable disk 
Aug 23 00:32:43 fedora17 udisksd[1181]: Mounted /dev/sdb at /run/media/guy/CONTOUR USB on behalf of uid 1000 
Aug 23 00:32:43 fedora17 udisksd[1181]: Mounted /dev/sdc at /run/media/guy/GLUCOFACTS on behalf of uid 1000  
```

---

