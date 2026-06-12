---
title: "Using Pyrit and CUDA in Karmic Koala"
date: 2009-12-07
forum: General Help
---

### Post by spartarra on 2009-12-07
Hello everyone,

I am trying to test WPA security, actually I am trying to break my own Wi-Fi connection.

For that purpose, I am using pyrit. Has someone worked with it? 
I am using,
pyrit -e <essid> -i </path/to/dictionary/*.lst> -r </path/to/captured/file/*.cap>
and it does nothing (1).

Adding to this I have been reading about CUDA and I am really impressed; but according to nVidia's webpage they haven't developed a driver for Karmic Koala; does anyone know anything about this stuff? 
My plan would be using CUDA not only with pyrit; Matlab would be the next step.

Thanks in advance,

Software:
OS: Karmic Koala
Pyrit: 0.2.5-dev (svn r192)

(1) Nothing means: 
$ pyrit -e <essid> -i </path/to/dictionary/*.lst> -r </path/to/captured/file/*.cap>
Pyrit 0.2.5-dev (svn r192) (C) 2008, 2009 Lukas Lueg [http://pyrit.googlecode.com](http://pyrit.googlecode.com)
This code is distributed under the GNU General Public License v3

Connecting to storage... connected

Usage: pyrit [options] command

Recognized options:
  -e    : Filters AccessPoint by ESSID
  -b    : Filters AccessPoint by BSSID
  -i    : Filename for input ('-' is stdin)
  -o    : Filename for output ('-' is stdout)
  -r    : Packet capture source in pcap-format
  -u    : URL of the storage-system to use

Recognized commands:
  analyze            : Analyze a packet-capture file
  attack_batch       : Attack a handshake with PMKs/passwords from the db
  attack_cowpatty    : Attack a handshake with PMKs from a cowpatty-file
  attack_db          : Attack a handshake with PMKs from the db
  attack_passthrough : Attack a handshake with passwords from a file
  batch              : Batchprocess the database
  benchmark          : Determine performance of available cores
  create_essid       : Create a new ESSID
  delete_essid       : Delete a ESSID from the database
  eval               : Count the available passwords and matching results
  export_cowpatty    : Export results to a new cowpatty file
  export_hashdb      : Export results to an airolib database
  export_passwords   : Export passwords to a file
  help               : Print this help
  import_passwords   : Import passwords from a file
  list_cores         : List available cores
  list_essids        : List all ESSIDs but don't count matching results
  passthrough        : Compute PMKs on the fly and write to stdout
  selftest           : Test all cores to ensure they compute correct results
  strip              : Strip packet-capture files to the relevant packets
  stripLive          : Capture relevant packets from a live capture-source
  verify             : Verify 10% of the results by recomputation

$

---

### Post by t0p on 2009-12-07
I've never used pyrit or CUDA.  When auditing wifi security, I've had a lot of success using the packages included in Backtrack 4.  In particular, aircrack-ng.  I'd definitely recommend Backtrack.

---

### Post by spartarra on 2009-12-07
I could use Backtrack, but I was planning to use Ubuntu (with nVidia support) to have a more powerful computer (instead of using a live-CD).

---

### Post by spartarra on 2009-12-07
Solved. I forgot adding attack_passthrough to my attack. 

Next step: Adding CUDA to Karmic Koala.

---

