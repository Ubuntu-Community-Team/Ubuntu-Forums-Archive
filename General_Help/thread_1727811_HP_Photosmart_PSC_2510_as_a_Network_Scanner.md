---
title: "HP Photosmart PSC 2510 as a Network Scanner"
date: 2011-04-13
forum: General Help
---

### Post by MrVas on 2011-04-13
In case anybody is still using a HP PSC 2510 (or 2710) Photosmart All-in-One printer, the following Perl script will allow you to use the printer as a network scanner. Although feeding the pages on at a time is a pain, it works pretty well for having to scan a document or two on the fly.

You will need to define your own document path ($path) and PRINTER_IP address.

```
#!/usr/bin/perl
#
#  AutoScan.pl - Automated document scanner
#

@types = ("JPG", "PDF", "TIFF");
@urlopt = ("jpg?id=8&type=3&size=1&fmt=2", "pdf?id=9&type=1&size=1&fmt=3", "tif?id=8&type=3&size=1&fmt=1");
$url = "http://<PRINTER_IP>/scan/image1.";

print "\n AutoScan.pl - Automated document scanner.\n\n";
print " Press <ENTER> to start, CTRL-C to exit, or enter scan type.\n";
&choices;

if ($^O eq "linux") {
  # Linux/Unix path
  $path = "/document/path";
} else {
  # Windows path
  $path = "C:/document/path";
}
unless (-d $path) {
  $path = ".";
}

while (<STDIN>) {
  if ($_ =~ /(0|1|2)/) { $type = $_; }
  elsif ($prev =~ /(0|1|2)/) { $type = $prev; }
  else { $type = 0; }
  $prev = $type;

  ($sec, $min, $hour, $mday, $mon, $year, $wday, $yday, $isdst) = localtime(time);
  $filename = "scan_" . sprintf "%4d%02d%02d%02d%02d%02d", $year+1900, $mon+1, $mday, $hour, $min, $sec;

  print "\n Scanning document to $path/$filename.$types[$type]\n";
  $cmd = "wget \"$url$urlopt[$type]\" -q -O $path/$filename.$types[$type]\n";
  qx/$cmd/;
  print "\n Press <ENTER> to continue, CTRL-C to exit, or enter scan type.\n";
  &choices;
}

sub choices {
  $msg = " [";
  for ($x = 0; $x < @types; $x++) {
    $msg .= "$x=$types[$x]";
    if ($x == $type) { $msg .= " (default)"; }
    if ($x =~ /^(0|1)$/) { $msg .= ", "; }  
    else { $msg .= "]: "; }
  }
  print $msg;
}
```Enjoy,

Vas

---

