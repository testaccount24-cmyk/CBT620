# CBT620
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 620 is from Hiroyuki Konishi and is an Assembler          *   FILE 620
//*           program which is a precompiler for COBOL programs,    *   FILE 620
//*           so you can copy pieces of code from members of a      *   FILE 620
//*           pds, to make a single source program to feed into     *   FILE 620
//*           the COBOL compiler.  See the member $SAMPJCL for      *   FILE 620
//*           sample JCL to run this program.                       *   FILE 620
//*                                                                 *   FILE 620
//*           The idea is to extend the concept of COPY members     *   FILE 620
//*           into any part of a COBOL program, not just the        *   FILE 620
//*           PROCEDURE DIVISION segments of code.                  *   FILE 620
//*                                                                 *   FILE 620
//*           Hiroyuki Konishi                                      *   FILE 620
//*           mailto:milkyw@gamma.ocn.ne.jp                         *   FILE 620
//*           http://www.milkyware.com/                             *   FILE 620
//*                                                                 *   FILE 620
//*    Purpose of the MWCBLCPY program:                             *   FILE 620
//*                                                                 *   FILE 620
//*     Normally in COBOL programs, COPY statements can only        *   FILE 620
//*     occur in the PROCEDURE DIVISION.  Using my program,         *   FILE 620
//*     you can put COPY statements anywhere in the COBOL           *   FILE 620
//*     program, and before compiling, you run the modified         *   FILE 620
//*     source (with the included COPY statements) through my       *   FILE 620
//*     program, and THEN into the COBOL compiler.  Please see      *   FILE 620
//*     member $SAMPJCL for more complete sample JCL.  My           *   FILE 620
//*     program will expand the COPY statements by copying the      *   FILE 620
//*     named pds member inline into the program source code.       *   FILE 620
//*                                                                 *   FILE 620
//*     As stated above, the COPY statement must begin in           *   FILE 620
//*     column 12, and the pds member name to be copied, must       *   FILE 620
//*     begin in column 17.  The member to be copied, must          *   FILE 620
//*     exist in the //SYSLIB library.                              *   FILE 620
//*                                                                 *   FILE 620
//*     Sample COBOL coding with COPY statements in the FILE        *   FILE 620
//*     SECTION.                                                    *   FILE 620
//*                                                                 *   FILE 620
//*    002700*                                                      *   FILE 620
//*    002800 FD  SAMPLE-FILE         BLOCK  0  RECORDS             *   FILE 620
//*    002900                         LABEL  RECORD  STANDARD       *   FILE 620
//*    003000                         RECORDING  MODE  IS  F.       *   FILE 620
//*    003100 01  SAMPLE-REC.                                       *   FILE 620
//*    003200     COPY SAMPREC.                                     *   FILE 620
//*    003300*                                                      *   FILE 620
//*                                                                 *   FILE 620
//*    I show a sample JCL in the following.  See also member       *   FILE 620
//*    $SAMPJCL for a more complete JCL example.                    *   FILE 620
//*                                                                 *   FILE 620
//*    //        EXEC PGM=MWCBLCPY,REGION=1024K                     *   FILE 620
//*    //STEPLIB   DD DSN=xxxx.xxxx.xxxx,DISP=SHR                   *   FILE 620
//*    //SYSLIB    DD DSN=xxxx.xxxx.xxxx,DISP=SHR  <= Copy lib      *   FILE 620
//*    //SYSIN     DD DSN=xxxx.xxxx.xxxx(xxxx),    <= Your COBOL    *   FILE 620
//*    //             DISP=SHR                     <= source code.  *   FILE 620
//*    //SYSLIN    DD DSN=&xxxx,DISP=(MOD,PASS),   <= Expanded      *   FILE 620
//*    //             UNIT=SYSDA,                  <= source, into  *   FILE 620
//*    //             SPACE=(80,(500,100))         <= compiler.     *   FILE 620
//*                                                                 *   FILE 620
```
