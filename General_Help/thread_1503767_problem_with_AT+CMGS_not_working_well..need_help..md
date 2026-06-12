---
title: "problem with AT+CMGS not working well..need help."
date: 2010-06-07
forum: General Help
---

### Post by madhav_palshikar on 2010-06-07
i wrote the php script for sending sms using PHP Direct io extension PHP-dio.
The same script works well in windows. but it gives problem in UBUNTU. Script goes well up to AT+CMGF....and when it reaches AT+CMGS ......it gets hang....! plz help me urgent.

here is the my script.....


<?php

set_time_limit(0);
exec('mode /dev/ttyS0 baud=9600 data=8 stop=1 parity=n ');
$fd = dio_open('/dev/ttyS0', O_RDWR, 0644);
if ($fd){
  dio_write($fd, "AT\r");
  $response="";
  while(1){
    $response.=dio_read($fd, 2);
//  $response.=dio_read($fd, 5);  // This will not work as it hangs the script here.
    $lines=ereg_replace("\r","",$response);
    $lines=explode("\n",$lines);
    if (in_array("OK",$lines)) break;
    if (in_array("ERROR",$lines)) break;
  }
  print_r($lines);
  
    dio_write($fd, "AT+CMGF=1\r");
  $response="";
  while(1){
    $response.=dio_read($fd, 2);
//  $response.=dio_read($fd, 5);  // This will not work as it hangs the script here.
    $lines=ereg_replace("\r","",$response);
    $lines=explode("\n",$lines);
    if (in_array("OK",$lines)) break;
    if (in_array("ERROR",$lines)) break;
  }
  print_r($lines);
    
        sleep(2);
        
      dio_write($fd, "AT+CMGS=\"+91xxxxxxxxxx\"");
      sleep(2);
      dio_write($fd, chr(13));
      sleep(1);
       dio_write($fd,"test123".chr(26).chr(13));
      sleep(1);
  $response="";
  while(1){
    $response.=dio_read($fd, 2);
//  $response.=dio_read($fd, 5);  // This will not work as it hangs the script here.
    $lines=ereg_replace("\r","",$response);
    $lines=explode("\n",$lines);
    if (in_array("OK",$lines)) break;
    if (in_array("ERROR",$lines)) break;
  }
  print_r($lines);

   dio_close($fd);

}

?>

   Thanx
Madhav Palshikar

---

### Post by madhav_palshikar on 2010-06-07
help me....

---

