---
title: "script to discover wireless clients"
date: 2010-12-06
forum: General Help
---

### Post by vttay03 on 2010-12-06
I need some help figuring out how to discover clients connected to my home router.  I've read up and can't seem to find a clear solution.  The one command I've come across that seems to be semi-reliable is :

```

nmap -sP 192.168.1.0/24

```

This seems to scan the IP address range of the router and return results.  However, it doesn't seem to always catch everyone that's connected and I get mixed results.  I'm also hoping to return the name of the computer in addition to the IP.  Does anyone have insight into this?  I want to come up with a script I can throw into cron or something that'll run once an hour and report who's connected to my router.

---

### Post by vttay03 on 2010-12-07
bump

anyone?

---

### Post by QLee on 2010-12-07
[QUOTE=vttay03]bump

anyone?[/QUOTE]
Easiest way is to look on the router itself, most (if not all) keep a list of connections, including IP address, hostname and MAC. Use your browser to access it, it will be explained in the router documentation

---

### Post by vttay03 on 2010-12-07
> 
Easiest way is to look on the router itself, most (if not all) keep a list of connections, including IP address, hostname and MAC. Use your browser to access it, it will be explained in the router documentation


Yeah I know how to do that.  I'm just always looking for things to mess around with in the terminal and thought it would be neat to spawn a bash script to check this every couple of hours.

---

### Post by vttay03 on 2010-12-08
Bump

anyone else out there with ideas?

---

### Post by Cheesehead on 2010-12-09
I use a python script to log into the router, pull the router's device list, compare the list against a set of criteria, and notify me of any unwelcome changes.

You must know exactly what information you want from the router, and where it is on the router's web pages. Some machines do not report their names to the router at all, so that info will be blank or '*'. Any devices that maintain a static IP address on your network (like some printers) also may be missing from router lists, since they do not have DHCP leases.

I keep a slightly-out-of-date list of all my MAC addresses in a whitelist. The script checks DHCP leases against the whitelist. A truly clever intruder can spoof the MAC address of a trusted machine, so it's not a perfect security solution.

Here's part of it in shell, and also in python:
```

#!/usr/bin/sh
RouterUsername="MY-ROUTER-USERNAME"
RouterPassword="MY-ROUTER-PASSWORD"
DeviceListUrl="http://192.168.1.1/DeviceList.asp"
echo "Running"
RouterDevices=$(wget -O - -o /dev/null $DeviceListUrl --user=$RouterUserName --password=$RouterPassword | grep 'var leases' | cut -d',' -f1-100 )
# Your 'grep' and 'cut' formatting will vary based on your router, of course.

```

```
#!/usr/bin/env python
#Python 2.7 script

import urllib2
import base64
import re
import string

router_username = "MY-ROUTER-USERNAME"
router_password = "MY-ROUTER-PASSWORD"
device_list_url = "http://192.168.1.1/DeviceList.asp"

base_64_string = base64.encodestring('%s:%s' % (router_username, router_password))[:-1]
authorization_header = "Basic %s" % base_64_string
request = urllib2.Request(device_list_url)
request.add_header("Authorization", authorization_header)
handle = urllib2.urlopen(request)

router_web_page = handle.readlines()
for line in router_web_page:
    if line.count("var leases = [") == 1:   #Your search criteria will vary by router
        print(line)
```

---

### Post by vttay03 on 2010-12-10
Thanks!  This is great stuff, especially since it's also showing me how to interactively login to a web page that requires a username and password.  I'm not at home right now but am going to give some of this a try later on...

But this is basically what I want, I still think there's a way to do it without logging into the router homepage but have yet to figure it out.

---

### Post by otkaz on 2010-12-10
cheeseheads solution is nice, but if it doesn't suit your needs 'arp -a' and 'dig' are easily scripted and useful commands.

---

### Post by Cheesehead on 2010-12-10
Is there a way to get arp to show devices on the same network that communicate with the router, but not directly with my machine? Every time I try arp, I only get my router and my printer...and there's more out there.

---

### Post by vttay03 on 2010-12-12
```

#!/usr/bin/env python
#Python 2.7 script

import urllib2
import base64
import re
import string

router_username = "MY-ROUTER-USERNAME"
router_password = "MY-ROUTER-PASSWORD"
device_list_url = "http://192.168.1.1/DeviceList.asp"

base_64_string = base64.encodestring('%s:%s' % (router_username, router_password))[:-1]
authorization_header = "Basic %s" % base_64_string
request = urllib2.Request(device_list_url)
request.add_header("Authorization", authorization_header)
handle = urllib2.urlopen(request)

router_web_page = handle.readlines()
for line in router_web_page:
    if line.count("var leases = [") == 1:   #Your search criteria will vary by router
        print(line)

```

I've confirmed this will get me to the initial login page, but it won't take the username and password I supplied it.  I was able to figure this out by redirecting stdout to a text file, and then viewing the page source after I visited it in a browser.  The page source and text file were identical, which indicates it never takes the login information.  Is there any apparent reason why this would be happening?  I've never used Python before so I am not able to easily debug...

---

### Post by rickyrockrat on 2010-12-12
have you tried arp-scan?
Here's a little guide:
[http://www.nta-monitor.com/wiki/index.php/Arp-scan_User_Guide](http://www.nta-monitor.com/wiki/index.php/Arp-scan_User_Guide)

---

### Post by Cheesehead on 2010-12-12
Does the shell version work?

What kind of response does it give you? 403 Auth error? Or something else?
Can you post the response HTML header?

---

### Post by vttay03 on 2010-12-12
Shell version gives the same response I believe...I captured the output to a text file, it's posted below (sorry it's difficult to parse but I didn't know exactly what to post, a majority of it appears to be C functions or something):

```

<!--- Page(9074)=[Login] ---><HTML><HEAD><META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8"><META HTTP-EQUIV="EXPIRES" CONTENT="Sun, 12 Dec 2010 16:28:28 GMT"><META HTTP-EQUIV="CACHE-CONTROL" CONTENT="NO-CACHE"><META HTTP-EQUIV="PRAGMA" CONTENT="NO-CACHE"><TITLE>Verizon</TITLE><STYLE type="text/css">BODY {color: #000000; font-family: Verdana, Helvetica, Arial, sans-serif; background-color: #D32000; background-image: url('images/gradientstrip.gif'); background-repeat: repeat-x; }

TD, INPUT, OPTION, SELECT {font-size: 11px}

TD.GRID {border-left:1px solid #ffffff;border-top:1px solid #ffffff; border-right:1px solid #CCCCCC;border-bottom:1px solid #CCCCCC; color: #000000;}

TD.GRID_NO_LEFT {border-left:0px;border-top:1px solid #ffffff; border-right:1px solid #CCCCCC;border-bottom:1px solid #CCCCCC; color: #000000;}

TD.GRID_NO_RIGHT {border-left:1px solid#ffffff; border-top:1px solid #ffffff; border-right:0px;border-bottom:1px solid #CCCCCC; color: #000000;}

.PAGE_HEADER {font-size: 14px;}

.REMARK {font-size: 9px;}

.BUTTON {cursor: pointer;}

.DATA {color: #000000;}

.actiontec_header {Font-Size:14px; font-weight:bold; color: black; text-align:center;}

.actiontec_red_header {Font-Size:14px; font-weight:bold; color: black; text-align:center; border-style:solid; border-width:1px; border-color:red;}

.actiontec_sub_header {Font-Size:12px; font-weight:bold; color: black;}

.actiontec_regular_text {font-size : 11px; line-height: 140%; color : black;}

.actiontec_regular_text_underline {font-size : 11px; line-height: 140%; color : black; text-decoration: underline;}

.actiontec_regular_text_bold {font-size : 11px; font-weight : bold; line-height: 140%; color : black;}

.actiontec_regular_text_bold_underline {font-size : 11px; font-weight : bold; font-style : normal; line-height: 140%; color : black; text-decoration: underline;}

.actiontec_small_text {Font-Size:11px; color: black; text-align:left;}

.actiontec_small_text_underline {Font-Size:11px; color: black; text-align:left; text-decoration: underline;}

.actiontec_big_text {Font-Size:12px; font-weight:bold; color: black; line-height: 140%; text-align:center;}

.actiontec_sidetab_normal {background-color:#E0E5F1; COLOR: #181C4C; TEXT-DECORATION: none; Font-Size:11px; border-top: solid #ffffff 2px;}

.actiontec_sidetab_selected {background-color: black; COLOR: white; TEXT-DECORATION: none; Font-Size:11px; border-top: solid #ffffff 2px;}

.actiontec_sidetab_selected A:link {color: white;}

.actiontec_sidetab_selected A:visited {color: white;}

.actiontec_sidetab_selected A:hover {color: white;}

.actiontec_button {background-color: #181C4C; border-color: #E0E5FF; border-style: solid; border-width: 3; border-top-width: 4; border-right-width: 4; border-left-width: 4; color: #FFFFFF; font-size : 11px;}

.actiontec_button A:link {color: white;}

@media all {  IE\:homepage {behavior:url(#default#homepage)} }

A {color: #000000;}

A:link {TEXT-DECORATION: none}

A:visited {TEXT-DECORATION: none}

A:hover {TEXT-DECORATION: underline}

TD.GRID A {color: #00286F;}

TD.GRID_NO_LEFT A {color: #00286F;}

TD.GRID_NO_RIGHT A {color: #00286F;}

TD.DATA A {color: #00286F;}



#hintbox{ /*CSS for pop up hint box */                     

position:absolute;                                         

top: 0;                                                    

background-color: lightyellow;                             

width: 150px; /*Default width of hint.*/                   

padding: 3px;                                              

border:1px solid black;                                    

font:normal 11px Verdana;                                  

line-height:18px;                                          

z-index:100;                                               

border-right: 3px solid black;                             

border-bottom: 3px solid black;                            

visibility: hidden;                                        

}                                                          

                                                           

.hintanchor{ /*CSS for link that shows hint onmouseover*/  

font-weight: bold;                                         

color: navy;                                               

margin: 3px 8px;                                           

}                                                          



</STYLE></HEAD><BODY alink=#000000 vlink=#000000 link=#000000 bgcolor=#D32000 topmargin=0 leftmargin=0 marginheight=0 marginwidth=0 onload=loaded()><FORM name="form_contents" method=POST action="index.cgi" enctype="application/x-www-form-urlencoded" onSubmit="if (window.is_submit && is_submit==1) return false; is_submit=1; return true; "><INPUT type=HIDDEN name="active_page" value="9074"><INPUT type=HIDDEN name="active_page_str" value="page_login"><INPUT type=HIDDEN name="page_title" value="Login"><INPUT type=HIDDEN name="mimic_button_field" value=""><INPUT type=HIDDEN name="button_value" value=""><INPUT type=HIDDEN name="strip_page_top" value="0"><SCRIPT language="Javascript"><!--

/*

 * A JavaScript implementation of the RSA Data Security, Inc. MD5 Message

 * Digest Algorithm, as defined in RFC 1321.

 * Version 2.1 Copyright (C) Paul Johnston 1999 - 2002.

 * Other contributors: Greg Holt, Andrew Kepert, Ydnar, Lostinet

 * Distributed under the BSD License

 * See http://pajhome.org.uk/crypt/md5 for more info.

 */



/*

 * Configurable variables. You may need to tweak these to be compatible with

 * the server-side, but the defaults work in most cases.

 */

var hexcase = 0;  /* hex output format. 0 - lowercase; 1 - uppercase        */

var b64pad  = ""; /* base-64 pad character. "=" for strict RFC compliance   */

var chrsz   = 8;  /* bits per input character. 8 - ASCII; 16 - Unicode      */



/*

 * These are the functions you'll usually want to call

 * They take string arguments and return either hex or base-64 encoded strings

 */

function hex_md5(s){ return binl2hex(core_md5(str2binl(s), s.length * chrsz));}

function b64_md5(s){ return binl2b64(core_md5(str2binl(s), s.length * chrsz));}

function str_md5(s){ return binl2str(core_md5(str2binl(s), s.length * chrsz));}

function hex_hmac_md5(key, data) { return binl2hex(core_hmac_md5(key, data)); }

function b64_hmac_md5(key, data) { return binl2b64(core_hmac_md5(key, data)); }

function str_hmac_md5(key, data) { return binl2str(core_hmac_md5(key, data)); }



/* 

 * Perform a simple self-test to see if the VM is working 

 */

function md5_vm_test()

{

  return hex_md5("abc") == "900150983cd24fb0d6963f7d28e17f72";

}



/*

 * Calculate the MD5 of an array of little-endian words, and a bit length

 */

function core_md5(x, len)

{

  /* append padding */

  x[len >> 5] |= 0x80 << ((len) % 32);

  x[(((len + 64) >>> 9) << 4) + 14] = len;

  

  var a =  1732584193;

  var b = -271733879;

  var c = -1732584194;

  var d =  271733878;



  for(var i = 0; i < x.length; i += 16)

  {

    var olda = a;

    var oldb = b;

    var oldc = c;

    var oldd = d;

 

    a = md5_ff(a, b, c, d, x[i+ 0], 7 , -680876936);

    d = md5_ff(d, a, b, c, x[i+ 1], 12, -389564586);

    c = md5_ff(c, d, a, b, x[i+ 2], 17,  606105819);

    b = md5_ff(b, c, d, a, x[i+ 3], 22, -1044525330);

    a = md5_ff(a, b, c, d, x[i+ 4], 7 , -176418897);

    d = md5_ff(d, a, b, c, x[i+ 5], 12,  1200080426);

    c = md5_ff(c, d, a, b, x[i+ 6], 17, -1473231341);

    b = md5_ff(b, c, d, a, x[i+ 7], 22, -45705983);

    a = md5_ff(a, b, c, d, x[i+ 8], 7 ,  1770035416);

    d = md5_ff(d, a, b, c, x[i+ 9], 12, -1958414417);

    c = md5_ff(c, d, a, b, x[i+10], 17, -42063);

    b = md5_ff(b, c, d, a, x[i+11], 22, -1990404162);

    a = md5_ff(a, b, c, d, x[i+12], 7 ,  1804603682);

    d = md5_ff(d, a, b, c, x[i+13], 12, -40341101);

    c = md5_ff(c, d, a, b, x[i+14], 17, -1502002290);

    b = md5_ff(b, c, d, a, x[i+15], 22,  1236535329);



    a = md5_gg(a, b, c, d, x[i+ 1], 5 , -165796510);

    d = md5_gg(d, a, b, c, x[i+ 6], 9 , -1069501632);

    c = md5_gg(c, d, a, b, x[i+11], 14,  643717713);

    b = md5_gg(b, c, d, a, x[i+ 0], 20, -373897302);

    a = md5_gg(a, b, c, d, x[i+ 5], 5 , -701558691);

    d = md5_gg(d, a, b, c, x[i+10], 9 ,  38016083);

    c = md5_gg(c, d, a, b, x[i+15], 14, -660478335);

    b = md5_gg(b, c, d, a, x[i+ 4], 20, -405537848);

    a = md5_gg(a, b, c, d, x[i+ 9], 5 ,  568446438);

    d = md5_gg(d, a, b, c, x[i+14], 9 , -1019803690);

    c = md5_gg(c, d, a, b, x[i+ 3], 14, -187363961);

    b = md5_gg(b, c, d, a, x[i+ 8], 20,  1163531501);

    a = md5_gg(a, b, c, d, x[i+13], 5 , -1444681467);

    d = md5_gg(d, a, b, c, x[i+ 2], 9 , -51403784);

    c = md5_gg(c, d, a, b, x[i+ 7], 14,  1735328473);

    b = md5_gg(b, c, d, a, x[i+12], 20, -1926607734);



    a = md5_hh(a, b, c, d, x[i+ 5], 4 , -378558);

    d = md5_hh(d, a, b, c, x[i+ 8], 11, -2022574463);

    c = md5_hh(c, d, a, b, x[i+11], 16,  1839030562);

    b = md5_hh(b, c, d, a, x[i+14], 23, -35309556);

    a = md5_hh(a, b, c, d, x[i+ 1], 4 , -1530992060);

    d = md5_hh(d, a, b, c, x[i+ 4], 11,  1272893353);

    c = md5_hh(c, d, a, b, x[i+ 7], 16, -155497632);

    b = md5_hh(b, c, d, a, x[i+10], 23, -1094730640);

    a = md5_hh(a, b, c, d, x[i+13], 4 ,  681279174);

    d = md5_hh(d, a, b, c, x[i+ 0], 11, -358537222);

    c = md5_hh(c, d, a, b, x[i+ 3], 16, -722521979);

    b = md5_hh(b, c, d, a, x[i+ 6], 23,  76029189);

    a = md5_hh(a, b, c, d, x[i+ 9], 4 , -640364487);

    d = md5_hh(d, a, b, c, x[i+12], 11, -421815835);

    c = md5_hh(c, d, a, b, x[i+15], 16,  530742520);

    b = md5_hh(b, c, d, a, x[i+ 2], 23, -995338651);



    a = md5_ii(a, b, c, d, x[i+ 0], 6 , -198630844);

    d = md5_ii(d, a, b, c, x[i+ 7], 10,  1126891415);

    c = md5_ii(c, d, a, b, x[i+14], 15, -1416354905);

    b = md5_ii(b, c, d, a, x[i+ 5], 21, -57434055);

    a = md5_ii(a, b, c, d, x[i+12], 6 ,  1700485571);

    d = md5_ii(d, a, b, c, x[i+ 3], 10, -1894986606);

    c = md5_ii(c, d, a, b, x[i+10], 15, -1051523);

    b = md5_ii(b, c, d, a, x[i+ 1], 21, -2054922799);

    a = md5_ii(a, b, c, d, x[i+ 8], 6 ,  1873313359);

    d = md5_ii(d, a, b, c, x[i+15], 10, -30611744);

    c = md5_ii(c, d, a, b, x[i+ 6], 15, -1560198380);

    b = md5_ii(b, c, d, a, x[i+13], 21,  1309151649);

    a = md5_ii(a, b, c, d, x[i+ 4], 6 , -145523070);

    d = md5_ii(d, a, b, c, x[i+11], 10, -1120210379);

    c = md5_ii(c, d, a, b, x[i+ 2], 15,  718787259);

    b = md5_ii(b, c, d, a, x[i+ 9], 21, -343485551);



    a = safe_add(a, olda);

    b = safe_add(b, oldb);

    c = safe_add(c, oldc);

    d = safe_add(d, oldd);

  }

  return Array(a, b, c, d);

  

}



/*

 * These functions implement the four basic operations the algorithm uses.

 */

function md5_cmn(q, a, b, x, s, t)

{

  return safe_add(bit_rol(safe_add(safe_add(a, q), safe_add(x, t)), s),b);

}

function md5_ff(a, b, c, d, x, s, t)

{

  return md5_cmn((b & c) | ((~b) & d), a, b, x, s, t);

}

function md5_gg(a, b, c, d, x, s, t)

{

  return md5_cmn((b & d) | (c & (~d)), a, b, x, s, t);

}

function md5_hh(a, b, c, d, x, s, t)

{

  return md5_cmn(b ^ c ^ d, a, b, x, s, t);

}

function md5_ii(a, b, c, d, x, s, t)

{

  return md5_cmn(c ^ (b | (~d)), a, b, x, s, t);

}



/*

 * Calculate the HMAC-MD5, of a key and some data

 */

function core_hmac_md5(key, data)

{

  var bkey = str2binl(key);

  if(bkey.length > 16) bkey = core_md5(bkey, key.length * chrsz);



  var ipad = Array(16), opad = Array(16);

  for(var i = 0; i < 16; i++) 

  {

    ipad[i] = bkey[i] ^ 0x36363636;

    opad[i] = bkey[i] ^ 0x5C5C5C5C;

  }



  var hash = core_md5(ipad.concat(str2binl(data)), 512 + data.length * chrsz);

  return core_md5(opad.concat(hash), 512 + 128);

}



/*

 * Add integers, wrapping at 2^32. This uses 16-bit operations internally

 * to work around bugs in some JS interpreters.

 */

function safe_add(x, y)

{

  var lsw = (x & 0xFFFF) + (y & 0xFFFF);

  var msw = (x >> 16) + (y >> 16) + (lsw >> 16);

  return (msw << 16) | (lsw & 0xFFFF);

}



/*

 * Bitwise rotate a 32-bit number to the left.

 */

function bit_rol(num, cnt)

{

  return (num << cnt) | (num >>> (32 - cnt));

}



/*

 * Convert a string to an array of little-endian words

 * If chrsz is ASCII, characters >255 have their hi-byte silently ignored.

 */

function str2binl(str)

{

  var bin = Array();

  var mask = (1 << chrsz) - 1;

  for(var i = 0; i < str.length * chrsz; i += chrsz)

    bin[i>>5] |= (str.charCodeAt(i / chrsz) & mask) << (i%32);

  return bin;

}



/*

 * Convert an array of little-endian words to a string

 */

function binl2str(bin)

{

  var str = "";

  var mask = (1 << chrsz) - 1;

  for(var i = 0; i < bin.length * 32; i += chrsz)

    str += String.fromCharCode((bin[i>>5] >>> (i % 32)) & mask);

  return str;

}



/*

 * Convert an array of little-endian words to a hex string.

 */

function binl2hex(binarray)

{

  var hex_tab = hexcase ? "0123456789ABCDEF" : "0123456789abcdef";

  var str = "";

  for(var i = 0; i < binarray.length * 4; i++)

  {

    str += hex_tab.charAt((binarray[i>>2] >> ((i%4)*8+4)) & 0xF) +

           hex_tab.charAt((binarray[i>>2] >> ((i%4)*8  )) & 0xF);

  }

  return str;

}



/*

 * Convert an array of little-endian words to a base-64 string

 */

function binl2b64(binarray)

{

  var tab = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/";

  var str = "";

  for(var i = 0; i < binarray.length * 4; i += 3)

  {

    var triplet = (((binarray[i   >> 2] >> 8 * ( i   %4)) & 0xFF) << 16)

                | (((binarray[i+1 >> 2] >> 8 * ((i+1)%4)) & 0xFF) << 8 )

                |  ((binarray[i+2 >> 2] >> 8 * ((i+2)%4)) & 0xFF);

    for(var j = 0; j < 4; j++)

    {

      if(i * 8 + j * 6 > binarray.length * 32) str += b64pad;

      else str += tab.charAt((triplet >> 6*(3-j)) & 0x3F);

    }

  }

  return str;

}



function SendPassword()

{

    var tmp;

    document.form_contents.elements['md5_pass'].value=document.form_contents.elements['passwordmask_1847409634'].value+document.form_contents.elements['auth_key'].value

    tmp=hex_md5(document.form_contents.elements['md5_pass'].value);

    document.form_contents.elements['md5_pass'].value=tmp;

    document.form_contents.elements['passwordmask_1847409634'].value="";

    mimic_button('submit_button_login_submit: ..', 1);

}



var is_button_in_focus=false;

var is_textarea_in_focus=false;

var is_submit=0;

var is_loaded=0;

var timer=0;

var suppress_keystroke=0;



function loaded()

{

  var inp;



  is_loaded=1;

  if (inp)

  {

     if (inp.type != 'hidden')

       inp.focus();

  }

}

function keyDown(e)

{

  var button_no;

  return true;

  switch (button_no)

  {

  case 13:

    if (is_button_in_focus || is_textarea_in_focus)

      return true;

    SendPassword();

    return false;

  case 32:

    if (is_button_in_focus)

    {

    SendPassword();

      return false;

    }

    return true;

  default:

    if (suppress_keystroke)

    {

      suppress_keystroke = 0;

      return false;

    }

    return true;

  }

}



document.onkeydown=keyDown;

function mimic_button(button_name,use_default_cgi)

{

  if (is_submit)

    return;

  f=document.form_contents;

  f.mimic_button_field.value = button_name;

  is_submit=1;

  setTimeout("is_submit=0", 4000);

  if (timer)

  {

    clearTimeout(timer);

    timer = 0;

  }

  if (use_default_cgi)

  {

    f.encoding = "application/x-www-form-urlencoded";

    f.action = "index.cgi";

  }

  f.submit();

}

function set_cgi(action,encoding)

{

  f=document.form_contents;

  f.encoding=encoding;

  f.action=action;

}





// -->

</SCRIPT><TABLE border=0 cellpadding=0 cellspacing=0 width="100%"><TR><TD rowspan=3>&nbsp;</TD><TD valign=BOTTOM height="95" width="10%"><TABLE border=0 cellpadding=4 cellspacing=0 width="100%"><TR><TD width="4%">&nbsp;</TD><TD align=LEFT valign=BOTTOM><MAP name="logo"><AREA title="" alt="" onFocus="is_button_in_focus=true;" onBlur="is_button_in_focus=false;"href="http://www.verizon.com" shape=rectangle coords="0,0,185,40"  TARGET="_blank"></MAP><IMG border=0 src="/images/vz_logo.gif" name="vz_logo" width="185" height="40" usemap="#vz"></TD><TD width="4%">&nbsp;</TD></TR></TABLE></TD><TD rowspan=3>&nbsp;</TD></TR><TR><TD width="10%"><TABLE border=0 cellpadding=0 cellspacing=0 width="100%"><TR><TD valign=TOP><TABLE border=0 cellpadding=0 cellspacing=0 width="100%"></TABLE></TD><TD valign=TOP><TABLE border=0 cellpadding=0 cellspacing=0 width="100%"><TR><TD align=LEFT valign=BOTTOM height="15" width="16"><IMG border=0 src="/images/actiontec_lt_top_corner.gif" name="actiontec_lt_top_corner" width="16" height="15"></TD><TD background="/images/actiontec_top_bar.gif" align=CENTER valign=BOTTOM><IMG border=0 src="/images/empty.gif" name="empty" width="800" height="2"></TD><TD align=RIGHT valign=BOTTOM><IMG border=0 src="/images/actiontec_rt_top_corner.gif" name="actiontec_rt_top_corner" width="24" height="15"></TD></TR><TR><TD background="/images/actiontec_lt_col.gif"><IMG border=0 src="/images/empty.gif" name="empty" width="2" height="2"></TD><TD bgcolor=#FFFFFF><TABLE border=0 cellpadding=0 cellspacing=0 width="100%"><TR><TD valign=TOP><TABLE border=0 cellpadding=0 cellspacing=0 width="100%"><TR><TD bgcolor=#FFFFFF align=CENTER valign=MIDDLE colspan=3><P><BR></P></TD></TR><TR><TD bgcolor=#FFFFFF align=CENTER valign=MIDDLE><IMG border=0 src="/images/empty.gif" name="empty" width="8" height="2"></TD><TD bgcolor=#FFFFFF align=CENTER valign=MIDDLE width="100%"><TABLE border=0 cellpadding=0 cellspacing=0><TR><TD bgcolor=#FFFFFF align=LEFT valign=MIDDLE><B><FONT size=3 color=#000000 face="Verdana, Helvetica, Arial, sans-serif"><SPAN  class=PAGE_HEADER>&nbsp;Login</SPAN></FONT></B></TD></TR></TABLE><BR><TABLE border=0 cellpadding=4 cellspacing=0 width="60%"><TR><TD align=LEFT valign=MIDDLE colspan=2><TABLE border=0 cellpadding=4 cellspacing=0 width="100%"><TR bgcolor=#E0E5F1><TD class="GRID_NO_RIGHT" align=LEFT valign=MIDDLE width="50%"><B>User Name</B>:</TD><TD class="GRID_NO_LEFT" align=LEFT valign=MIDDLE width="50%"><INPUT type=HIDDEN name="user_name_defval" value=""><INPUT type=TEXT style="WIDTH: 150px" name="user_name" value="" size=20 maxlength=64 ></TD></TR><TR bgcolor=#F1F3F9><TD class="GRID_NO_RIGHT" align=LEFT valign=MIDDLE width="50%"><B>Password</B>:</TD><TD class="GRID_NO_LEFT" align=LEFT valign=MIDDLE width="50%"><INPUT type=hidden name="passwordmask_1847409634" id=pass1 ><INPUT type=PASSWORD style="WIDTH: 150px" id=pass2 name="passwd1" value="" size=20 maxlength=64 onkeyup="if (event.keyCode == 8){pass1.value=pass1.value.substring(0, pass1.value.length-1); pass2.value=pass2.value.substring(0,pass2.value.length-1);if (pass2.value.length == 0) pass1.value='';} else if (event.keyCode !=13) {pass1.value+=pass2.value.replace(/(^[\s]*)|([\s]*$)/g, ''); if (pass2.value.length == 1) pass2.value='   '; else if (pass2.value.length == 4) pass2.value = '     '; else if (pass2.value.length == 6) pass2.value='       ';  else if (pass2.value.length == 8) pass2.value='         '; else if (pass2.value.length == 10) pass2.value='            '; else if (pass2.value.length == 13) pass2.value='               '; else if (pass2.value.length == 16) pass2.value='                  '; else if (pass2.value.length == 19) pass2.value='                   '; else if (pass2.value.length == 20) pass2.value='                  '; else if (pass2.value.length >= 21) pass2.value='                    '; else if (pass2.value.length > 1 && pass2.value.length != 4 && pass2.value.length != 6 && pass2.value.length != 8 && pass2.value.length != 10 && pass2.value.length != 13 && pass2.value.length != 19 && pass2.value.length != 20) pass2.value='       ';}" ><INPUT type=HIDDEN name="md5_pass" value=""></TD></TR></TABLE></TD></TR></TABLE><INPUT type=HIDDEN name="auth_key" value="444322883"><CENTER><TABLE border=0 cellpadding=0 cellspacing=0><TR><TD height="5"><IMG border=0 src="/images/empty.gif" name="empty" width="2" height="5"></TD></TR></TABLE><TABLE border=0 cellpadding=0 cellspacing=0><TR><TD align=CENTER valign=MIDDLE><SPAN  onclick="SendPassword()"><TABLE border=0 cellpadding=0 cellspacing=0><TR><TD class="actiontec_button" align=CENTER valign=MIDDLE height="25"><SPAN  onclick="return false;" style="margin: 15px;"><A HREF="onclick="SendPassword()"">OK</A></SPAN></TD></TR></TABLE></SPAN></TD></TR></TABLE></CENTER></TD><TD bgcolor=#FFFFFF align=CENTER valign=MIDDLE width="8"><IMG border=0 src="/images/empty.gif" name="empty" width="8" height="2"></TD></TR><TR><TD bgcolor=#FFFFFF align=CENTER valign=MIDDLE colspan=3><P><BR></P></TD></TR></TABLE></TD></TR></TABLE></TD><TD background="/images/actiontec_rt_col.gif"><IMG border=0 src="/images/empty.gif" name="empty" width="2" height="2"></TD></TR><TR><TD align=LEFT valign=TOP><IMG border=0 src="/images/actiontec_lt_btm_corner.gif" name="actiontec_lt_btm_corner" width="16" height="25"></TD><TD background="/images/actiontec_btm_bar.gif" align=CENTER valign=TOP><IMG border=0 src="/images/empty.gif" name="empty" width="2" height="2"></TD><TD align=RIGHT valign=TOP height="25" width="24"><IMG border=0 src="/images/actiontec_rt_btm_corner.gif" name="actiontec_rt_btm_corner" width="24" height="25"></TD></TR></TABLE></TD></TR></TABLE></TD></TR><TR><TD colspan=3 height="500">&nbsp;</TD></TR></TABLE></FORM></BODY></HTML>


```

---

### Post by Cheesehead on 2010-12-12
The shell and python HTTP authentication scripts won't work because the page you posted does not use normal HTTP authentication. Instead it uses javascript to mask your password and securely send it to the server (gateway).

Most of the page is javascript functions to encrypt your password before sending. Unless you're an expert at creating encrypted HTTP post actions, or deciphering javascript, it may not be worth your while to script it directly.

Does your router, by chance, permit ssh connections? (unlikely, but ever hopeful). Or does the router have settings to change the security scheme?

---

### Post by vttay03 on 2010-12-13
No, my router doesn't appear to accept SSH connections or have the ability to alter its security settings.  I believe I may look into arp-scan as mentioned above.  This appears to be a slightly different tool than 'arp', which I didn't have much luck with either.

---

### Post by Cheesehead on 2010-12-14
Agreed. Arp-scan, instead of logging into the router, seems much easier in this case.

Interestingly, on my network, I need to run about 5-10 ping cycles for everything on my network to reply. Thanks, rickyrockrat, for pointing me towards arp-scan.

---

### Post by vttay03 on 2010-12-14
Cheesehead - you may know how to do this as well, you seem to be good with scripting.

Let's say I run arp-scan and get an output similar to what's posted below:

```

192.168.0.2    00:11:22:33:44:55
192.168.0.3    66:77:88:99:AA:BB

```

How could I then strip out the MAC addresses and compare them against known good ones.  For instance if I defined two variables at the top of the script like:

```

VALID1=00:11:22:33:44:55
VALID2=AB:CD:EF:12:34:56

```

In this case the first MAC address recognized by arp-scan would be OK, and then second one a possible intrusion.  I'd want the output of the script to appear something like:

```

192.168.0.2    00:11:22:33:44:55    OK
192.168.0.3    66:77:88:99:AA:BB    WARNING!!

```

I think there's way to do this with sed but I'm not good with sed, so I'm not sure how.  My output of arp-scan may be slightly off, but I think that's the general appearance.  I'm not at home right now so I can't recall exactly how it looks.

---

### Post by vttay03 on 2010-12-15
Ok, so I've sorta got the guts of it completed.  Basically it will parse the output of 'arp-scan' line by line, extract the MAC address and compare it against known good ones.  Since it's scanning the output line by line, it can append "OK" or "WARNING" on the end of each line.  See code below...I had been using a text file as sample input but I think I can just change the end of the while loop to read stdin from 'arp-scan'.

```

#!/bin/bash

FILENAME="sample_out.txt"
count=0
MAC1="11:22:33:44:55:66"
MAC2="77:88:99:AA:BB:CC"
TEMP_MAC=""


# Begin by running arp-scan and capturing output to text file

# Read in file line by line
while read LINE
do
  let count++
  if [[ ${LINE:0:1} == "1" ]]; then # test to see if it's an IP address
    for ((i=0; i<${#LINE}; i++)) # loop through characters on line finding first colon
    do
      if [[ ${LINE:i:1} == ":" ]]; then 
        TEMP_MAC=${LINE:i-2:17} # MAC address begins two characters prior to colon
        break
      fi
    done
    if [[ $TEMP_MAC == $MAC1 ]] || [[ $TEMP_MAC == $MAC2 ]]; then # test extracted MAC address against known good ones
      echo -e "$LINE\tOK" # append OK if match
    else
      echo -e "$LINE\tWARNING" # append warning if no match
    fi
  fi
done < $FILENAME

echo -e "\nTotal $count lines read"

```

---

