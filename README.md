Production folder `fitness2019/` 
===============================

> INRA\[Olivier Vitrac](mailto:olivier.vitrac@agroparistech.fr), rev. Aug 20, 2019

Generate static website for lectures of Sept 2019 in Freising, Germany.

[TOC]

## Test sites

The following machines have been locally installed;

| machine    | URL                                                          |
| ---------- | ------------------------------------------------------------ |
| LX-Olivier | http://10.75.4.112/fitness/html/lectures, http://192.168.1.47/fitness/html/lectures |
| mol12      | http://192.168.1.7/fitness/html/lectures                     |
| mol15      | http://mol15.agroparistech.fr/fitness/html/lectures          |

## Design of lectures

The content of the different lectures are organized as follows.

```bash
.
├── fitness _ common training modules
│   ├── session 1 _ what is food packaging
│   │   ├── unit 1.1 panorama of food packaging
│   │   ├── unit 1.2 packaging materials and shaping process
│   │   └── unit 1.3 basic legal framework
│   ├── session 2 _ properties of food packaging materials
│   │   ├── unit 2.1 thermal, mechanical and barrier properties
│   │   ├── unit 2.2 food preservation technology and packaging
│   │   └── unit 2.3 chemical and physical stability of packaging materials
│   ├── session 3 _ packaging and food preservation
│   │   ├── unit 3.1 common physical chemical factors affecting food stability
│   │   └── unit 3.2 food packaging and shelf life
│   └── session 4 _ innovations in food packaging
│       ├── unit 4.1 biobased and biodegradable materials
│       ├── unit 4.2 active packaging
│       ├── unit 4.3 smart packaging
│       └── unit 4.4 nanotechnology strategies
└── fitness _ specialized training modules
    ├── session 1 _ risk assessment
    │   ├── unit 1.1 hazar identification and characterization
    │   └── unit 1.2 exposure assesment and risk characterization
    ├── session 2 _ decision making and advanced risk management techniques
    │   ├── unit 2.1 introduction to decision theory and risk management
    │   ├── unit 2.2 managing uncertainty by intervals and worst-case scenarios
    │   └── unit 2.3 probabilistic approaches and bayesian approaches
    ├── session 3 _ legislation regulation of food contact materials
    │   ├── unit 3.1 eu legislation, national regulations, us regulations, others
    │   └── unit 3.2 gmp and quality assurance standards
    ├── session 4 _ mass transfer in food packaging
    │   ├── unit 4.1 principles of mass transfer
    │   ├── unit 4.2 migration modelling for monomaterials
    │   ├── unit 4.3 modelling for multi-materials, multi-steps process
    │   ├── unit 4.4 calculation of permeability in composite system
    │   ├── unit 4.5 multicomponent diffusion, predictive models
    │   └── unit 4.6 micro holes and leaks in packaging
    ├── session 5 _ fmeca applied to food packaging design
    │   ├── unit 5.1 history and principles of fmea-fmeca
    │   ├── unit 5.2 diagram-based approaches
    │   └── unit 5.3 computer-aided approaches
    ├── session 6 _ molecular and thermodynamical modeling
    │   ├── unit 6.1 principles (forcefields, statistical-ensembles), overview of online databases
    │   ├── unit 6.2 microscopic theories of transport coefficients and free-energies
    │   └── unit 6.3 calculations using fluctuation theorems
    ├── session 7 _ eco-design
    │   ├── unit 7.1 methodologies used in life cycle assessment
    │   ├── unit 7.2 tools for life cycle imppact assessment
    │   └── unit 7.3 application to the choice of the material etc
    └── session 8 _ forming, filling and sealing processes
        ├── unit 8.1 shaping and forming
        ├── unit 8.2 filling
        ├── unit 8.3 closing - sealing
        ├── unit 8.5 surface treatments and coatings
        └── unit 8.6 printing and labeling
```



## File structure

> ==Folders may look duplicated due to the presence of a mix of upper and lower cases.==
>
> The current file structure reflects the current state of the conversion
```bash
fitness2019/
│
│ ~~~~~~~ INPUTS ~~~~~~~
│
├── download20190810 (or any equivalent)    <--- SOURCE FILES
│   ├── fileidentification_template.xlsx    <--- future implementation
│   │
│   ├── fitness _ common training modules   <--- add PPT files to any modules
│   ├── FITNESS _ COMMON TRAINING MODULES
│   ├── fitness _ specialized training modules
│   ├── FITNESS _ SPECIALIZED TRAINING MODULES
│   ├── FITNESS _ TRAINING MODULES.zip    
│   │
│   ├── hash                                 <--- long path fix (not to be modified)
│   │
│   ├── How to convert ppt in image ppt file.pptx
│   ├── How to revise the units.pptx
│   ├── PREFETCH_extractTXTfromPPT_How to convert ppt in image ppt file.mat
│   ├── PREFETCH_extractTXTfromPPT_How to revise the units.mat
│   └── WP2_Materials_fitness.xlsx
│
│
├── Fitness-logo128x128.png      <--- logo files
├── Fitness-logo256x256.png
├── Fitness-logo64x64.png
├── Fitness logo RVB.png         <=== this logo is used to create the main index
│
│ ~~~~~~~ ENGINE ~~~~~~~
│
├── matlab
│   ├── alias.m
│   ├── extractTXTfromPPT.m
│   ├── fileid_20190814.m       <=== MAIN SCRIPT (it requires ../sandbox/fileid_20190814.ods)
│   ├── makepptxindex.m
│   ├── makewww_20190810.ods    <--- not used (see fileidentification_template.xlsx)
│   ├── pptx2reveal_v2.m
│   └── sandbox                 <--- development folder (not used)
│
├── README                      <--- this file
│
│ ~~~~~~~ OUTPUTS ~~~~~~~
│
└── sandbox
    ├── fileid_20190814.ods     <=== MAIN PATH DEFINITIONS TO BUILD THE STATIC WEB SITE
	│   					     (aliases $INPUT1,$INPUT2.... are updated by the script 	│    						 ../matlab/fileid_20190814.m)
    └── www20190814             <=== www/ root folder corresponding to
    							./fileid_20190814.ods and ../matlab/fileid_20190814.m
```

## Input folder `download20190810/`

> ==The concepts of sessions and sections are mixed.==

It has been assumed that a lecture could be identified as:

|      MODULES       |  SESSION  |       UNIT       |    PPT FILE    |
| :----------------: | :-------: | :--------------: | :------------: |
|      $level$       | $section$ |      $unit$      |   $lecture$    |
| *common, advanced* |  *1..8*   | *1.1, 1.2, etc.* | *part1, part2* |



### Main sessions = $level$

```bash
.
├── fitness _ common training modules
│   ├── session 1 _ what is food packaging
│   ├── Session 1 _ What is food packaging
│   ├── session 2 _ properties of food packaging materials
│   ├── Session 2 _ Properties of food packaging materials
│   ├── session 3 _ packaging and food preservation
│   ├── Session 3 _ Packaging and food preservation
│   ├── session 4 _ innovations in food packaging
│   └── Session 4 _ Innovations in food packaging
├── FITNESS _ COMMON TRAINING MODULES
│   ├── Session 1 _ What is food packaging
│   ├── Session 2 _ Properties of food packaging materials
│   ├── Session 3 _ Packaging and food preservation
│   └── Session 4 _ Innovations in food packaging
├── fitness _ specialized training modules
│   ├── session 4 _ mass transfer in food packaging
│   ├── Session 4 _ Mass transfer in food packaging
│   ├── Session 5 _ FMECA applied to food packaging design
│   ├── Session 6 _ Molecular and thermodynamical modeling
│   ├── Session 7 _ Eco-design
│   └── Session 8 _ Forming, filling and sealing processes
├── FITNESS _ SPECIALIZED TRAINING MODULES
│   ├── Session 1 _ Risk assessment
│   ├── Session 2 _ Decision making and advanced risk management techniques
│   ├── Session 3 _ Legislation Regulation of food contact materials
│   ├── session 4 _ mass transfer in food packaging
│   ├── Session 4 _ Mass transfer in food packaging
│   ├── Session 5 _ FMECA applied to food packaging design
│   ├── Session 6 _ Molecular and thermodynamical modeling
│   ├── Session 7 _ Eco-design
│   └── Session 8 _ Forming, filling and sealing processes

```

### Sections and sub-sections = $section.unit$

```bash
.
├── session 1 _ what is food packaging
│   ├── Unit 1.1 Panorama of food packaging
│   ├── Unit 1.2 Packaging materials and shaping process
│   └── Unit 1.3 Basic legal framework
├── Session 1 _ What is food packaging
│   ├── Unit 1.1 Panorama of food packaging
│   ├── Unit 1.2 Packaging materials and shaping process
│   └── Unit 1.3 Basic legal framework
├── session 2 _ properties of food packaging materials
│   ├── Unit 2.1 thermal, mechanical and barrier properties
│   ├── Unit 2.2 Food preservation technology and packaging
│   └── Unit 2.3 Chemical and physical stability of packaging materials
├── Session 2 _ Properties of food packaging materials
│   ├── Unit 2.1 thermal, mechanical and barrier properties
│   ├── Unit 2.2 Food preservation technology and packaging
│   └── Unit 2.3 Chemical and physical stability of packaging materials
├── session 3 _ packaging and food preservation
│   └── Unit 3.1 Common physical chemical factors affecting food stability
├── Session 3 _ Packaging and food preservation
│   ├── Unit 3.1 Common physical chemical factors affecting food stability
│   └── Unit 3.2 Food packaging and shelf life
├── session 4 _ innovations in food packaging
│   ├── Unit 4.1 Biobased and biodegradable materials
│   ├── Unit 4.2 Active packaging
│   ├── Unit 4.3 Smart packaging
│   └── Unit 4.4 Nanotechnology strategies
└── Session 4 _ Innovations in food packaging
    ├── Unit 4.1 Biobased and biodegradable materials
    ├── Unit 4.2 Active packaging
    ├── Unit 4.3 Smart packaging
    └── Unit 4.4 Nanotechnology strategies

```

### PPT files=$lecture$

```
├── session 1 _ what is food packaging
│   ├── Unit 1.1 Panorama of food packaging
│   │   └── UZAG PBF (sharing materials) - Unit 1.1 (Common) Panorama of food packaging
│   ├── Unit 1.2 Packaging materials and shaping process
│   │   ├── Fitness_Unit_1.2-Cork
│   │   ├── Fitness_Unit_1.2-Metal_FP_3
│   │   ├── Fitness_Unit_1.2-Plastic_2
│   │   ├── UCP - Fitness_Unit_1.2-Glass 07032019
│   │   └── UCP - Fitness_Unit_1.2-Paper and Paperboard 08032019
│   └── Unit 1.3 Basic legal framework
│       ├── 20-12-18 - Unit 1.3 (Common) - Basic legal framework - ACTIA-LNE
│       └── UZAG PBF (sharing materials) - Unit 1.3 (Common)  Basic legal framework
├── Session 1 _ What is food packaging
│   ├── Unit 1.1 Panorama of food packaging
│   ├── Unit 1.2 Packaging materials and shaping process
│   └── Unit 1.3 Basic legal framework

```

### Where to add exported static images of your PPT

 Export your entire presentation in the same location in PNG at 300 dpi, without changing the name of the file.

1. In PowerPoint, open your slide presentation, and then open the slide that you want to export.
2. On the **File** menu, select **Save As**.
3. In the **Save as type** box, select one of the following picture formats:
   - GIF Graphics Interchange Format (.gif)
   - JPEG File Interchange Format (*.jpg)
   - PNG Portable Network Graphics Format (*.png)

Do not change the picture's save location in the **Save in** box and do not to change the name of the picture in the **File name** box.

1. Select **Save**. You will be prompted with the following dialog box:

   ![Select Current Slide Only.](https://support.microsoft.com/Library/Images/2881255.jpg)

   Select **Every Slide**. 

2. Please check the the slides are saved at 300 dpi. Right-click the picture, and then select **Properties**. The size should be 3201 × 2397 pixels (or something close)



```bash
.
├── 20-12-18 - Unit 1.3 (Common) - Basic legal framework - ACTIA-LNE/ <=== PNG folder
│   ├── Slide10.PNG
~~~~~~~
│   ├── Slide8.PNG
│   └── Slide9.PNG
├── 20-12-18 - Unit 1.3 (Common) - Basic legal framework - ACTIA-LNE.pptx <=== PPTX
├── PREFETCH_extractTXTfromPPT_20-12-18 - Unit 1.3 (Common) - Basic legal framework - ACTIA-LNE.mat  <==== PPTX text extraction (prefetched)
~~~~~~~~~
├── PREFETCHPPTx_pptx2reveal_v2_UZAG PBF (sharing materials) - Unit 1.3 (Common)  Basic legal framework.mat   
├── UZAG PBF (sharing materials) - Unit 1.3 (Common)  Basic legal framework
│   ├── Slide10.PNG
~~~~~~~~
│   ├── Slide6.PNG
│   ├── Slide7.PNG
│   ├── Slide8.PNG
│   └── Slide9.PNG
└── UZAG PBF (sharing materials) - Unit 1.3 (Common)  Basic legal framework.pptx

```



## Output folder `www20190814/`

### How it works

Currently, all the structure is reconstructed automatically from the file organization and the content of PPTx. 

### Folder organization

```bash
.
└── www20190814                 <=== wwwroot (usually http://somewebsite/fitness/)
    └── lectures                <===== folder containing lectures
        ├── html                <===== HTML content
        │   ├── common           <================ $level
        │   │   ├── S1           <================== $section
        │   │   │   ├── U1.1     <===================== $unit
        │   │   │   │   ├── part1.html <=============== $lecture
        │   │   │   │   └── src_part1/ <=============== slides of $lecture
        │   │   │   ├── U1.2
        │   │   │   │   ├── part1.html
        │   │   │   │   ├── part2.html
        │   │   │   │   ├── part3.html
        │   │   │   │   ├── part4.html
        │   │   │   │   ├── part5.html
        │   │   │   │   ├── src_part1
        │   │   │   │   ├── src_part2
        │   │   │   │   ├── src_part3
        │   │   │   │   ├── src_part4
        │   │   │   │   └── src_part5
        │   │   │   └── U1.3
        │   │    
        ~~~~~~
        │   │            
        │   │            
        │   ├── index.html                      <=================== main index file
        │   │ 
        ~~~~~~
        │   │    
        │   └── specialized
        │       ├── S3
        │       │   ├── U3.1
        │       │   │   ├── part1.html
        │       │   │   ├── part2.html
        │       │   │   ├── src_part1
        │       │   │   └── src_part2
        │       │   └── U3.2
         │   │ 
        ~~~~~~
        │   │  
        └── src                  <===== HTML content
            ├── css
            │   ├── highlight
            │   ├── print
            │   └── theme
            │       ├── source
            │       └── template
            ├── js
            ├── lib
            │   ├── css
            │   ├── font
            │   │   ├── league-gothic
            │   │   └── source-sans-pro
            │   └── js
            └── plugin
                ├── highlight
                ├── markdown
                │   └── example.html
                ├── math
                ├── multiplex
                ├── notes
                │   └── notes.html
                ├── notes-server
                │   └── notes.html
                ├── print-pdf
                ├── search
                └── zoom-js

```

## Miscellaneous

### How to change the export resolution in PowerPoint

> Source: https://docs.microsoft.com/en-us/office/troubleshoot/powerpoint/change-export-slide-resolution

By default, the export resolution of a PowerPoint slide that you want to save as a picture is 96 dots per inch (dpi). To change the export resolution, follow these steps:

1. Exit all Windows-based programs.

2. Right-click the **Start** button and then **Run**. (In Windows 7, select **Start**, and then **Run**.)

3. In the **Open** box, type regedit, and then select **OK**.

4. Locate one of the following registry subkeys, depending on the version of PowerPoint that you're using:

   PowerPoint 2016

   **HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\PowerPoint\Options**

   PowerPoint 2013

   **HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\PowerPoint\Options**

   PowerPoint 2010

   **HKEY_CURRENT_USER\Software\Microsoft\Office\14.0\PowerPoint\Options**

   PowerPoint 2007

   **HKEY_CURRENT_USER\Software\Microsoft\Office\12.0\PowerPoint\Options**

   PowerPoint 2003

   **HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\PowerPoint\Options**

5. Click the **Options** subkey, point to **New** on the **Edit** menu, and then click **DWORD Value**.

6. Type ExportBitmapResolution, and then press Enter.

7. Make sure that **ExportBitmapResolution** is selected, and then click **Modify** on the **Edit** menu.

8. In the Edit DWORD Value dialog box, select **Decimal**.

9. In the **Value data** box, type the value of the resolution that you want such as 300.

10. Select **OK**.

11. On the **File** menu, select **Exit** to exit Registry Editor.

