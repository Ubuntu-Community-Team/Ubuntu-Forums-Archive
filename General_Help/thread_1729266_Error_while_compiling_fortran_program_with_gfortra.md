---
title: "Error while compiling fortran program with gfortran"
date: 2011-04-14
forum: General Help
---

### Post by JCM_Pico on 2011-04-14
Hello there

I've a FORTRAN program that I would like to compile in my machine.
I've gfortran installed, so I issue the command:
gfortran asc2bin.f  write_geogrid.o

but this error are displayed

```
asc2bin.f:3.72:

      INTEGER isigned,i,j,endian,wordsize,nx,ny,xllcorner,yllcorner,    
                                                                        1
Error: Invalid character in name at (1)
asc2bin.f:4.7:

      & cellsize,missvalue,nz                                           
       1
Error: Invalid character in name at (1)
asc2bin.f:44.72:

      call write_geogrid(rarray,nx,ny,nz,isigned,endian,scalefactor,    
                                                                        1
Error: Syntax error in argument list at (1)
asc2bin.f:45.7:

      & wordsize)                                                       
       1
Error: Invalid character in name at (1)

```
And here is the fortran code

```
      PROGRAM asc2bin

      INTEGER isigned,i,j,endian,wordsize,nx,ny,xllcorner,yllcorner,
      & cellsize,missvalue,nz
      REAL scalefactor
      ALLOCATABLE rarray(:,:),iarray(:,:),barray(:,:)
      CHARACTER*20 head12

      isigned = 1
      endian = 1
      wordsize = 2
      scalefactor = 1.0
      nz = 1
      print*,'nz',nz
      open(10,file='srtm_36_04.asc')
      read(10,*)head12,nx
      read(10,*)head12,ny
      read(10,*)head12,xllcorner
      read(10,*)head12,yllcorner
      read(10,*)head12,cellsize
      read(10,*)head12,missvalue
      print*,'nx,ny',nx,ny,xllcorner,yllcorner,cellsize,missvalue
      allocate(rarray(nx,ny))
      allocate(iarray(nx,ny))

      do j = 1, ny
          read(10,*)iarray(:,j)
      enddo

      do i = 1, nx
          do j = 1, ny
          rarray(i,j)=iarray(i,ny-j+1)
          enddo
      enddo

      do j = 1, ny
          do i = 1, nx
          if(iarray(i,ny-j+1) .lt. 0) then
          rarray(i,j) = 0
          endif
          enddo
      enddo

      call write_geogrid(rarray,nx,ny,nz,isigned,endian,scalefactor,
      & wordsize)
      print*,'Rarray2',rarray(6000,5631)
      deallocate(rarray)

      stop
      end

```Can any one help to solve the problem?

---

### Post by gaitonde on 2011-04-15
[SIZE=2]At two places you have an ampersand (&) in column 7.  Move it to column 6.  

I could reproduce your errors gfortran on ubuntu 10.04.[/SIZE] [SIZE=2]
After moving the ampersand to column 6 at two places, the program compiles without errors.
But it does not create an a.out, since a subprogram is missing.

UNG[/SIZE]

---

