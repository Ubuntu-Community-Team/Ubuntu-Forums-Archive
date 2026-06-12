---
title: "With bash scripting how to answer any prompts automatically?"
date: 2012-03-23
forum: General Help
---

### Post by GRX13 on 2012-03-23
I'm very new to to bash in Ubuntu and i've written my first script revolving around generating SSL certificates with OpenSSL. I've automated the whole process from start to finish from making a private key, making a certificate authority and finishing with the actual certificate. The script gets to a point where it runs a single command and OpenSSL asks for some prompts to be filled one after the other:

```
Country Name (2 letter code) [AU]:
State or Province Name (full name) [Some-State]:
Locality Name (eg, city) []:
Organization Name (eg, company) [Internet Widgits Pty Ltd]:
Organizational Unit Name (eg, section) []:
Common Name (eg, YOUR name) []:
Email Address []:
```I've looked at Expect and <<EOF/EOF and i'm not sure how to use them really. Expect has a spawn command that works with network locations however everything I want to be filled in is located inside of my bash script and not somewhere else. [command] <<EOF just doesn't work and i'm thinking because there's many prompts from one command.

What can I do?

---

### Post by codemaniac on 2012-03-23
you can put all the arguments you want to pass to openssl in a input file called **input_args_file  **, and then invoke openssl .
something like .
```
cat input_args_file | openssl_script
```

contents of input_args_file can contain something like below .
```
Country_Name="AU"
State_or_Province_Name="Some-State"
Locality_Name="xxx"
Organization_Name="Internet Widgits Pty Ltd"
Organizational_Unit_Name="section"
Common_Name="xyz"
Email_Address="addas@xxx.com"
```

---

### Post by codemaniac on 2012-03-23
a sample non-interactive script to demonstrate the concept .
**nonInteractive.sh**
```
echo "Enter your name :"
read name
echo "Enter your emp Id :"
read eid

echo "$name""|"$eid
```
**usage**
```
echo -e "codemaniac\n99999999" | nonInteractive.sh
```

---

### Post by GRX13 on 2012-03-23
I don't like to avoid using a second file please.

---

### Post by codemaniac on 2012-03-23
> **Groxxxy said:**
> I don't like to avoid using a second file please.

Then pass your arguments to the script from echo as shown in the above example .

---

### Post by GRX13 on 2012-03-23
I'd like to avoid using a second file please.*

excuse me.

I've used: echo -e "codemaniac\n99999999" | nonInteractive.sh

There are more than one prompts. I don't see how that would work.

---

### Post by codemaniac on 2012-03-23
Can you also post the script you have tried so far , with the openssl command line ?

---

### Post by codemaniac on 2012-03-23
> **Groxxxy said:**
> I'd like to avoid using a second file please.*

excuse me.

I've used: echo -e "codemaniac\n99999999" | nonInteractive.sh

There are more than one prompts. I don't see how that would work.
The purpose behind the script was to demonstrate how to make a script noninteractive .It wont prompt you to enter data if pipe the arguments with echo . Got it ?

---

### Post by GRX13 on 2012-03-23
```
#! /bin/bash
root=~/Desktop/SSL
subroot1=Keys
subroot2=Certs
private=private.key
CA=ca.pem
device=device.key
certificate=certificate.crt
while [ answer != "0" ] 
do 
clear
echo "0 Exit"
echo "1 Do everything from start to finish with minimal prompts"
echo "2 Do everything from start to finish with prompts"
echo "3 Create private key"
echo "4 Create certificate authority"
echo "5 Create network device key, CSR, self-sign and certificate"
echo "-----------------------------------------------------------"
echo "A|a Make RAND file for backend website management"
echo "B|b Make PFX file (Depends on a present Certificate)"
echo "Select an option by entering corresponding number/letter:" 
read answer
    case $answer in
       1)
mkdir $root
mkdir $root/$subroot1
openssl genrsa -out $root/$subroot1/$private 2048
mkdir $root/$subroot2
openssl req -x509 -new -nodes -key $root/$subroot1/$private -days 9999 -out $root/$subroot2/$CA
#Creates directory "Certs" for Cert Authority and creates CA permission file
```

That's part of it. It gets to the last command and asks the prompts one after the other like in my first post. I want the script to fill them in saving me from doing so. With pre-determined inputs somewhere else in the script of course.

---

### Post by codemaniac on 2012-03-23
try something like below ..
```
case $answer in
       1)
#set your variables here
Country_Name="AU"
State_or_Province_Name="Some-State"
Locality_Name="xxx"
Organization_Name="Internet Widgits Pty Ltd"
Organizational_Unit_Name="section"
Common_Name="xyz"
Email_Address="addas@xxx.com"

mkdir $root
mkdir $root/$subroot1
openssl genrsa -out $root/$subroot1/$private 2048
mkdir $root/$subroot2
# try passing variables to openssl
echo -e "$Country_Name\n$State_or_Province_Name\n$Locality_Name\n$Organization_Name\n$Organizational_Unit_Name\n$Common_Name\n$Email_Address" | openssl req -x509 -new -nodes -key $root/$subroot1/$private -days 9999 -out $root/$subroot2/$CA
#Creates directory "Certs" for Cert Authority and creates CA permission file
```

---

### Post by GRX13 on 2012-03-23
Sorry, it says the string is too long. I think the echo is entering all of it at once.
I'd like to give Expect another go but actually use it properly. Don't know where to begin. All the google searches show it being used with the Spawn command with network locations.

---

### Post by codemaniac on 2012-03-23
pass all your arguments with -subj switch to openssl.

```
openssl req -x509 -new -nodes -key $root/$subroot1/$private -days 9999 -subj "/C=AU/ST=state/L=Locality/O=organization/CN=www.example.com" -out $root/$subroot2/$CA
```

---

### Post by codemaniac on 2012-03-23
[http://www.openssl.org/docs/apps/req.html#EXAMPLES](http://www.openssl.org/docs/apps/req.html#EXAMPLES)

---

### Post by GRX13 on 2012-03-23
:-o
You are a proper smartypants :-)
Works perfectly thank you Codemaniac; oh and happy 200 beans!

---

### Post by codemaniac on 2012-03-23
Great to hear that , i have also learnt something on openssl .Thank you .

---

