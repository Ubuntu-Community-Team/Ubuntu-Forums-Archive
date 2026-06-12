---
title: "How do I parse nmap output to grab IP &amp; MAC"
date: 2010-12-31
forum: General Help
---

### Post by J0hnnyBr@v0 on 2010-12-31
All,

I would like to parse an nmap outputfile, grab just the ip address and mac address info and output to another file.

For example:
Starting Nmap 5.35DC1 ( [http://nmap.org](http://nmap.org) ) at 2010-12-31 00:13 PST
Nmap scan report for 11.11.14.1
Host is up (0.00014s latency).
MAC Address: 00:16:EC:52:D8:AA (Elitegroup Computer Systems Co.)
Nmap scan report for 11.11.14.123
Host is up (0.037s latency).
MAC Address: 00:26:AB:46:6F:1F (Seiko Epson)
Nmap scan report for 11.11.14.127
Host is up.
Nmap scan report for 11.11.14.144
Host is up (0.031s latency).
MAC Address: 00:25:D3:CE:6D:7C (AzureWave Technologies)
Nmap scan report for 11.11.14.147
Host is up (0.0040s latency).
MAC Address: 00:16:CE:14:E6:59 (Hon Hai Precision Ind. Co.)
Nmap scan report for 11.11.14.150
Host is up (0.00011s latency).
MAC Address: E0:CB:4E:31:D5:A6 (Asustek Computer)
Nmap done: 256 IP addresses (6 hosts up) scanned in 2.49 seconds

Run it through a sed or grep/awk and have this as the output in another file:

11.11.14.1 00:16:EC:52:D8:AA -
11.11.14.123 00:26:AB:46:6F:1F -
11.11.14.144 00:25:D3:CE:6D:7C -
11.11.14.147 00:16:CE:14:E6:59 -
11.11.14.150 E0:CB:4E:31:D5:A6 -

Best Regards,
Eric

---

### Post by Crusty Old Fart on 2010-12-31
> **J0hnnyBr@v0 said:**
> All,

I would like to parse an nmap outputfile, grab just the ip address and mac address info and output to another file...

Don't have any idea why you wanted the dashes at the end of every line in the output file, but the script puts them in.

Here you go:
```

#!/bin/bash

echo -e "\nEnter the full path to the nmap output file to be parsed:"
read -e input_file

echo -e "\nEnter the full path to the output file from this script:"
read -e output_file

declare -a nmap_array=($(
  grep -e report -e MAC "$input_file" | \
  sed -e '{
    s/Nmap scan report for //g
    s/MAC Address: //g
    s/ (.\+//g
  }'
))

nmap_array_len=${#nmap_array[@]}
echo -n > "$output_file"

for (( i = 0; i <= $nmap_array_len; i++ )); do
  while (( $(echo ${nmap_array[$i]} | grep -c '[0-9A-F]\+:') < 1 )); do
    (( i++ ))
  done
  echo ${nmap_array[(( $i - 1 ))]} ${nmap_array[$i]} '-' >> "$output_file"
  (( i++ ))
done

echo -e "\nAll finished.\n" 
exit 0

```Happy New Year and stuff,

Crusty

---

### Post by J0hnnyBr@v0 on 2010-12-31
Thanks Crusty, as usual, you rock!

> **Crusty Old Fart said:**
> Don't have any idea why you wanted the dashes at the end of every line in the output file, but the script puts them in.

The only reason I want them is that is what the program wants.  If the program didn't want it...I wouldn't care.  Not real sure what they're for, but they're important...

Best Regards,
Eric

---

### Post by Crusty Old Fart on 2011-01-02
> **J0hnnyBr@v0 said:**
> Thanks Crusty, as usual, you rock!...
You're mighty welcome Eric, as always.

Still...If the assumptions that were made about the structure of the nmap output do not hold for every nmap run, the script could generate bogus parsings.

The following explanation of how the script was designed and how it works may serve to identify any exposures that may be embodied within it, which could result in unintended parsing output.

[B]Assumptions made regarding the structure of the nmap output:
[/B]
[LIST]
[*]Lines containing IP addresses will _always_ begin with the text string shown inside the following quotes: "Nmap scan report for ".
[*]Lines containing IP addresses will _never_ have anything after the IP address.
[*]Lines containing IP addresses will be the _only_ lines in the nmap output that contain the word: report
[*]Lines containing IP addresses will be omitted during parsing _unless_ a line containing a corresponding MAC address occurs in the nmap output _prior to_ the occurrence of _another_ line containing an IP address.
[*]Lines containing MAC addresses will _always_ begin with the text string shown inside the following quotes: "MAC Address: ".
[*]Lines containing MAC addresses will _never_ be followed by _anything_ that doesn't begin with a whitespace, a left parenthesis, and at least one other character, as shown between the following quotes: " (@", where @ represents any character.
[*]Lines containing MAC addresses will be the _only_ lines in the nmap output file that contain the word: MAC
[*]MAC address parameters will _always_ be delimited with a single colon between them.
[*]Alpha characters in MAC addresses will _never_ consist of anything other than the upper case characters A through F.
[*]There will _always_ be at least one line containing an IP address in between any two lines that contain MAC addresses.
[/LIST]
[B]Code interpretation:
[/B][INDENT]Consider the following block of code:
```

[COLOR=Green]**declare -a nmap_array=($(**[/COLOR]
[COLOR=Blue]**  grep -e report -e MAC "$input_file" | \**[/COLOR]
   [COLOR=Red][B] sed -e '{
    s/Nmap scan report for //g
    s/MAC Address: //g
    s/ (.\+//g
  }'[/B][/COLOR]
[COLOR=Green]**))**[/COLOR]

```The blue grep statement filters the contents of the nmap output file, which is named "input_file" in the script, and feeds only the lines containing the word: report, and the lines containing the word: MAC. through the pipe to the red sed construct on the lines below it. The lines containing the word: report, also contain the IP addresses, and the lines containing the word: MAC, also contain the MAC addresses.

The first substitution statement in the sed construct removes everything from the beginning of all the lines coming through the pipe that contain IP addresses, such that the only thing left on them are the IP addresses.

The second substitution statement removes everything from the beginning of the lines containing MAC addresses, such that all of those lines begin with MAC addresses.

The third substitution statement removes everything from the end of the lines containing MAC addresses, such that the only thing left on them are the MAC addresses.

Finally, the green lines wrap around this code block to perform a command substitution within the element section of an array declaration statement such that the array elements are each assigned one line of output coming through the grep/sed pipeline.

With the elements of the array having been assigned their values, the array contains every IP address and MAC address, interleaved with each other, one per element, in the exact order they occurred in the nmap output. One more parsing operation needs to be performed using this array to filter out IP addresses for which there is no corresponding MAC address. This parsing will be done with a while loop, nested within a for loop, that will find every MAC address, pair it with its corresponding IP address, concatenate these pairs on one line of output per pair with the IP address first, the MAC address second, with each line ending with a whitespace and a hyphen, and then written to a file, line by line in the correct order.

[br]2[/br]
Consider the following block of code, which performs the final parsing and output operations:
```

**[COLOR=Green]for (( i = 0; i <= $nmap_array_len; i++ )); do[/COLOR]**
[B][COLOR=Blue]  while (( $(echo ${nmap_array[$i]} | grep -c '[0-9A-F]\+:') < 1 )); do
    (( i++ ))
  done[/COLOR][/B]
[B][COLOR=Red]  echo ${nmap_array[(( $i - 1 ))]} ${nmap_array[$i]} '-' >> "$output_file"
  (( i++ ))[/COLOR][/B]
**[COLOR=Green]done[/COLOR]**

```The green lines in the code box above constitute the beginning and ending of a **for** loop that will explore the array containing the IP and MAC addresses. The loop counter (**i**) will not only be incremented by the starting **for** statement, but also from within the **for** loop construct. Internal incrementation of the counter will result in execution of the loop making fewer laps than otherwise would occur. This behavior is by design.

Within this **for** loop construct is a **while** loop shown in blue. It serves to increment the loop counter until a MAC address is found in the array.

When a MAC address is found, the red lines within the **for** construct are executed. The first red line pairs the MAC address contained in the **i**th element of the array, with the IP address in the preceding array element (**i** - 1), concatenates them, separated by one whitespace, with the IP address first, appends the concatenated address pair with a whitespace and a hyphen, and directs this entire concatenation as one line written to the script's output file.

[/INDENT]Rock on,

Crusty

---

