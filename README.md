# mirnas-downstream

#Implementation of a pipeline for downstream analysis of NGS data obtained after performing a dual RNA-SEQ experiment.

The pipeline is divided into several steps, each corresponding to a different directory, which have to be performed sequentially. As we enter into each directory, we will find the instructions written into a README file. The pipeline is divided as follows:
	
* **0_fq-files/** : Here we will need to have our input data as unzipped fastq (.fq) files.
* **1_fastqc/** : We will perform a quality control analysis of our input data by using FASTQC. 
* **2_mapper/** : We will make use of mapper.pl (from miRDeep2 software) to map our reads to a joint index of human and legionella.
* **3_quantifier/**: A quick quantification step by using quantifier.pl (from miRDeep2 software)
* **4_miRDeep/**: prediction of novel miRNAs

* **5_novel-miRNAs/**: processing of miRDeep2.pl output files for further analysis. Matrix of known and novel RCs. Dealing with duplicates.
* **6_rbb/** : reciprocal best blast hits of the top novel miRNAs against all mammals. Rbb against Legionella as well.
* **7_target-pred-and-interaction-networks/** : Differential expression analysis of miRNAs. Target prediction of novel miRNAs. Interaction networks of DE miRNAs - DE targets.

[example of seq+coord in one line](/project/ngs_marsico/Javier/novel_miRNAs_full_pipeline/4_novel_miRNAs/processed_miRNAs_sequences_coordinates_oneline_head.fa)


Expected output of step 7 after using cytoscape: 
[INTERACTION NETWORK EXAMPLE: GFPPT16](/home/rendon/Downloads/gfppt16better.pdf)


Put some directories in your .bashrc files, namely:
	
	    **(mapper.pl, quantifier.pl, miRDeep2.pl)**
    /project/ngs_marsico/Javier/bin/mirdeep2_0_0_8/src/
    
                        **(fastqc)**
	/project/ngs_marsico/Javier/bin/FastQC/
	

For all bash files, change source .bashrc to point to your own .bashrc file

        By default: source /home/rendon/.bashrc
