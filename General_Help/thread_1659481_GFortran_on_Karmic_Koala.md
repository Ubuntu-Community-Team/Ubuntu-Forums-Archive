---
title: "GFortran on Karmic Koala"
date: 2011-01-04
forum: General Help
---

### Post by raven128 on 2011-01-04
can't compile anything more complex than simple "Hello World". Even if i use additional compiler switches such as "-std=f95" or "-ffree-form", compiler doesn't work. and it isn't a coding error, not at all - i test these programs on windows - compiled just fine.

sample program:
```

program ifPrime

	integer x
	logical isPrime
	
	read *,x
	if (isPrime(x)) then
		print *, 'Prime'
	else
		print *, 'Non-Prime'
	end if

end program

function isPrime(x)
	logical isPrime
	integer x
	
	isPrime = .FALSE.
	i = 2	
	do while (i <= x/2)
		if (mod(x,i) == 0) then 
		  Exit
		 end if
	end do
	
	isPrime = .TRUE.
end function

```

GFortran output on compilation:
```

gfortran -Wall -c -ffree-form -std=f95 "test.f90" (&#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1077;: /home/xxxxxxxx/FProjects)
test.f90:3.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:4.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:6.1:
 read *,x
 1
Warning: Nonconforming tab character at (1)
test.f90:7.1:
 if (isPrime(x)) then
 1
Warning: Nonconforming tab character at (1)
test.f90:8.1:
  print *, 'Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:9.1:
 else
 1
Warning: Nonconforming tab character at (1)
test.f90:10.1:
  print *, 'Non-Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:11.1:
 end if
 1
Warning: Nonconforming tab character at (1)
test.f90:16.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:17.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:19.1:
 isPrime = .FALSE.
 1
Warning: Nonconforming tab character at (1)
test.f90:20.1:
 i = 2
 1
Warning: Nonconforming tab character at (1)
test.f90:21.1:
 do while (i <= x/2)
 1
Warning: Nonconforming tab character at (1)
test.f90:22.1:
  if (mod(x,i) == 0) then
 1
Warning: Nonconforming tab character at (1)
test.f90:23.1:
    Exit
 1
Warning: Nonconforming tab character at (1)
test.f90:24.1:
   end if
 1
Warning: Nonconforming tab character at (1)
test.f90:25.1:
 end do
 1
Warning: Nonconforming tab character at (1)
test.f90:27.1:
 isPrime = .TRUE.
 1
Warning: Nonconforming tab character at (1)
&#1057;&#1073;&#1086;&#1088;&#1082;&#1072; &#1087;&#1088;&#1086;&#1096;&#1083;&#1072; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086;.

```

GFortran output on build/make:
```

gfortran -Wall -o -ffree-form -std=f95 "test" "test.f90" (&#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1077;: /home/xxxxxxxxx/FProjects)
test.f90:3.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:4.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:6.1:
 read *,x
 1
Warning: Nonconforming tab character at (1)
test.f90:7.1:
 if (isPrime(x)) then
 1
Warning: Nonconforming tab character at (1)
test.f90:8.1:
  print *, 'Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:9.1:
 else
 1
Warning: Nonconforming tab character at (1)
test.f90:10.1:
  print *, 'Non-Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:11.1:
 end if
 1
Warning: Nonconforming tab character at (1)
test.f90:16.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:17.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:19.1:
 isPrime = .FALSE.
 1
Warning: Nonconforming tab character at (1)
test.f90:20.1:
 i = 2
 1
Warning: Nonconforming tab character at (1)
test.f90:21.1:
 do while (i <= x/2)
 1
Warning: Nonconforming tab character at (1)
test.f90:22.1:
  if (mod(x,i) == 0) then
 1
Warning: Nonconforming tab character at (1)
test.f90:23.1:
    Exit
 1
Warning: Nonconforming tab character at (1)
test.f90:24.1:
   end if
 1
Warning: Nonconforming tab character at (1)
test.f90:25.1:
 end do
 1
Warning: Nonconforming tab character at (1)
test.f90:27.1:
 isPrime = .TRUE.
 1
Warning: Nonconforming tab character at (1)
test: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/x86_64/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o:/build/buildd/eglibc-2.10.1/csu/../sysdeps/x86_64/elf/start.S:65: first defined here
test: In function `_fini':
(.fini+0x0): multiple definition of `_fini'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crti.o:(.fini+0x0): first defined here
test:(.rodata+0x0): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
test: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o:(.data+0x0): first defined here
test: In function `__data_start':
(.data+0x8): multiple definition of `__dso_handle'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/crtbegin.o:(.data+0x0): first defined here
test: In function `_init':
(.init+0x0): multiple definition of `_init'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crti.o:(.init+0x0): first defined here
/tmp/ccYZ8yyM.o: In function `MAIN__':
test.f90:(.text+0x0): multiple definition of `MAIN__'
test:(.text+0xe4): first defined here
/tmp/ccYZ8yyM.o: In function `isprime_':
test.f90:(.text+0x155): multiple definition of `isprime_'
test:(.text+0x239): first defined here
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
test:(.dtors+0x8): first defined here
/usr/bin/ld: warning: Cannot create .eh_frame_hdr section, --eh-frame-hdr ignored.
/usr/bin/ld: error in test(.eh_frame); no .eh_frame_hdr table will be created.
collect2: ld returned 1 exit status
&#1057;&#1073;&#1086;&#1088;&#1082;&#1072; &#1079;&#1072;&#1074;&#1077;&#1088;&#1096;&#1080;&#1083;&#1072;&#1089;&#1100; &#1089; &#1086;&#1096;&#1080;&#1073;&#1082;&#1086;&#1081;.

```

how can i fix it?

---

### Post by darmok47 on 2011-03-07
i dont know how is in windows, but in linux/unix (at least for Gfortran and Ifort) you have to declare variable like this

integer :: x

with '::'

try this and recompile simply with gfortran -o nameout namefale.fxx

---

### Post by gmargo on 2011-03-07
It's the tab characters.

If you reformat that source code by expanding all of the tabs into 8 spaces, the compile works.

---

### Post by simpli on 2011-11-08
> **raven128 said:**
> can't compile anything more complex than simple "Hello World". Even if i use additional compiler switches such as "-std=f95" or "-ffree-form", compiler doesn't work. and it isn't a coding error, not at all - i test these programs on windows - compiled just fine.

sample program:
```

program ifPrime

	integer x
	logical isPrime
	
	read *,x
	if (isPrime(x)) then
		print *, 'Prime'
	else
		print *, 'Non-Prime'
	end if

end program

function isPrime(x)
	logical isPrime
	integer x
	
	isPrime = .FALSE.
	i = 2	
	do while (i <= x/2)
		if (mod(x,i) == 0) then 
		  Exit
		 end if
	end do
	
	isPrime = .TRUE.
end function

```

GFortran output on compilation:
```

gfortran -Wall -c -ffree-form -std=f95 "test.f90" (&#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1077;: /home/xxxxxxxx/FProjects)
test.f90:3.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:4.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:6.1:
 read *,x
 1
Warning: Nonconforming tab character at (1)
test.f90:7.1:
 if (isPrime(x)) then
 1
Warning: Nonconforming tab character at (1)
test.f90:8.1:
  print *, 'Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:9.1:
 else
 1
Warning: Nonconforming tab character at (1)
test.f90:10.1:
  print *, 'Non-Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:11.1:
 end if
 1
Warning: Nonconforming tab character at (1)
test.f90:16.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:17.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:19.1:
 isPrime = .FALSE.
 1
Warning: Nonconforming tab character at (1)
test.f90:20.1:
 i = 2
 1
Warning: Nonconforming tab character at (1)
test.f90:21.1:
 do while (i <= x/2)
 1
Warning: Nonconforming tab character at (1)
test.f90:22.1:
  if (mod(x,i) == 0) then
 1
Warning: Nonconforming tab character at (1)
test.f90:23.1:
    Exit
 1
Warning: Nonconforming tab character at (1)
test.f90:24.1:
   end if
 1
Warning: Nonconforming tab character at (1)
test.f90:25.1:
 end do
 1
Warning: Nonconforming tab character at (1)
test.f90:27.1:
 isPrime = .TRUE.
 1
Warning: Nonconforming tab character at (1)
&#1057;&#1073;&#1086;&#1088;&#1082;&#1072; &#1087;&#1088;&#1086;&#1096;&#1083;&#1072; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086;.

```

GFortran output on build/make:
```

gfortran -Wall -o -ffree-form -std=f95 "test" "test.f90" (&#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1077;: /home/xxxxxxxxx/FProjects)
test.f90:3.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:4.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:6.1:
 read *,x
 1
Warning: Nonconforming tab character at (1)
test.f90:7.1:
 if (isPrime(x)) then
 1
Warning: Nonconforming tab character at (1)
test.f90:8.1:
  print *, 'Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:9.1:
 else
 1
Warning: Nonconforming tab character at (1)
test.f90:10.1:
  print *, 'Non-Prime'
 1
Warning: Nonconforming tab character at (1)
test.f90:11.1:
 end if
 1
Warning: Nonconforming tab character at (1)
test.f90:16.1:
 logical isPrime
 1
Warning: Nonconforming tab character at (1)
test.f90:17.1:
 integer x
 1
Warning: Nonconforming tab character at (1)
test.f90:19.1:
 isPrime = .FALSE.
 1
Warning: Nonconforming tab character at (1)
test.f90:20.1:
 i = 2
 1
Warning: Nonconforming tab character at (1)
test.f90:21.1:
 do while (i <= x/2)
 1
Warning: Nonconforming tab character at (1)
test.f90:22.1:
  if (mod(x,i) == 0) then
 1
Warning: Nonconforming tab character at (1)
test.f90:23.1:
    Exit
 1
Warning: Nonconforming tab character at (1)
test.f90:24.1:
   end if
 1
Warning: Nonconforming tab character at (1)
test.f90:25.1:
 end do
 1
Warning: Nonconforming tab character at (1)
test.f90:27.1:
 isPrime = .TRUE.
 1
Warning: Nonconforming tab character at (1)
test: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/x86_64/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o:/build/buildd/eglibc-2.10.1/csu/../sysdeps/x86_64/elf/start.S:65: first defined here
test: In function `_fini':
(.fini+0x0): multiple definition of `_fini'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crti.o:(.fini+0x0): first defined here
test:(.rodata+0x0): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
test: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o:(.data+0x0): first defined here
test: In function `__data_start':
(.data+0x8): multiple definition of `__dso_handle'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/crtbegin.o:(.data+0x0): first defined here
test: In function `_init':
(.init+0x0): multiple definition of `_init'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crti.o:(.init+0x0): first defined here
/tmp/ccYZ8yyM.o: In function `MAIN__':
test.f90:(.text+0x0): multiple definition of `MAIN__'
test:(.text+0xe4): first defined here
/tmp/ccYZ8yyM.o: In function `isprime_':
test.f90:(.text+0x155): multiple definition of `isprime_'
test:(.text+0x239): first defined here
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
test:(.dtors+0x8): first defined here
/usr/bin/ld: warning: Cannot create .eh_frame_hdr section, --eh-frame-hdr ignored.
/usr/bin/ld: error in test(.eh_frame); no .eh_frame_hdr table will be created.
collect2: ld returned 1 exit status
&#1057;&#1073;&#1086;&#1088;&#1082;&#1072; &#1079;&#1072;&#1074;&#1077;&#1088;&#1096;&#1080;&#1083;&#1072;&#1089;&#1100; &#1089; &#1086;&#1096;&#1080;&#1073;&#1082;&#1086;&#1081;.

```

how can i fix it?
hi, why dont you try 
gfortran -Wtabs program-name.f90

the "Warning: Nonconforming tab character&#8221; is only because of the &#8220;tabs&#8221;. If you replace tabs by spaces this warning will not come. But still you can bypass this tab warning by this option in gfortran.

Hope you have already solved the problem as its too late for the reply.

---

### Post by bksaur on 2012-07-28
thanks simpli!
Following yours suggestion, my problem is solved.
In fortran 90, the warning message  "Warning: Nonconforming tab character&#8221; appears if you use "tab" button in the keyboard. To get a nice code with comments far from statements, use multiple "space" bar, instead of "tab" key.

---

