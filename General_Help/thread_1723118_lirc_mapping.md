---
title: "lirc mapping"
date: 2011-04-06
forum: General Help
---

### Post by sr_guy on 2011-04-06
I want to use the following to map keys to emulate a mouse. If the following keys already are mapped for something else would this cause a conflict?

begin
	        prog=irexec
	        remote=Streamzap_PC_Remote
	        button=UP
	        config=xte "mousermove 0 -23"
	        repeat=1
end
	 
begin
                prog=irexec
	        remote=Streamzap_PC_Remote
	        button=DOWN
	        config=xte "mousermove 0 23"
	        repeat=1
end
	 
begin
	        prog=irexec
	        remote=Streamzap_PC_Remote
	        button=LEFT
	        config=xte "mousermove -23 0"
	        repeat=1
end
	 
begin
	        prog=irexec
	        remote=Streamzap_PC_Remote
	        button=RIGHT
	        config=xte "mousermove 23 0"
	        repeat=1
end
	 
begin
	        prog=irexec
	        remote=Streamzap_PC_Remote
	        button=OK
	        config=xte "mouseclick 3"
end

---

