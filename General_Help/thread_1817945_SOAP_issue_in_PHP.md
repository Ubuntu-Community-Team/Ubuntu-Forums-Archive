---
title: "SOAP issue in PHP"
date: 2011-08-04
forum: General Help
---

### Post by ramkumarpandian on 2011-08-04
Hi 

Iam trying to pass a array to the soap constructor but I coudnt

this what I am doing 
CLIENT FILE
$client = new SoapClient("qq.wsdl",$s_passwords);

SERVER FILE
$server = new SoapServer("qq.wsdl");
$server->setClass("qq",$password);

SERVER FILE CLASS
class qq
{
function qq()
{

}
}

please help me with the wsdl

Thank you
Ramkumar

---

