### VC6 Ultimate adjustment
I found VC6 Ultimate and try to use it. But I found that there are some problems while you use it. Below is my adjustments.    
1. Download VC6 Ultimate frome GitLab: https://gitlab.com/VC6Ultimate    
2. Uncompress. Create shortcuts via run create_shortcuts.js (double click to run).    
3. Run CMD with Administrator, enter to VisualUltimate\Addins\Visual Assist X\, run regsvr32 VAssist.dll     
4. Copy FileTool.dll to VC6Ultimate\Addins\, run regsvr32 FileTool.dll. Add below into AddIns block of VisualUltimate\VS_Config\DevStudio#6.0.hjson file. 
	"AddIns":{
......
		"FileTool.DSAddIn.1":{
			"":"1"
			"Description'":"Adds commands to Developer Studio which perform useful functions"
			"DisplayName":"FileTool Developer Studio Add-in"
			"Filename":"..\\..\\..\\VisualUltimate\\AddIns\\FileTool.dll"
		}
	}
When you new file and save, VC6 will hang and crash. Maybe this is a workaround. See also: https://www.betaarchive.com/wiki/index.php/Microsoft_KB_Archive/241396   
5. I suffer font of Document View. Copy YaHei.Consolas.1.12.ttf to VisualUltimate\Fonts folder, and all replace HobTiny to YaHei Consolas Hybrid in VisualUltimate\VS_Config\DevStudio#6.0.hjson file.   
6. The projects created by project template CAN NOT compile pass. I modified these templates. Copy and paste Project_Templates to VisualUltimate\Project_Templates and replace the files with same name.    
7. Some resources can't be compiled. rc.exe shipped with VC6Ultimate can't compile resource from VC6 wizard project. I change to official rc.exe, but there is a compatibility problem. official rc.exe is not compatible with win10, but it can run. It is simple to rewrite rc.exe, because whole of functions is at rcdll.dll. I decompile official and recompile it. You can replace it with the rc.exe I recompiled when you get a RCXXXX error.    
8. Can't load libclang.dll when launch. You need install Visual C++ 2015 Redistributable Package x86 version, because VC6 Ultimate is only x86 version. You can download it from https://aka.ms/vs/16/release/vc_redist.x86.exe or https://www.microsoft.com/zh-CN/download/details.aspx?id=48145. 
Document View can't show file content when you open a file. It is an opengl render problem. Usually it occurred in virtual machine. I have no way to resolve it even though soft opengl.    
9. Document View is not subclassed by VAX. Tested and abandoned addins：WndTab is not stable. VCExtend can't zoomin. VC6LineNumerAddin can't display.    
10. Editor only supports ASCII. Sometimes debug can't stop via Shift+F5. Not support WIN64 debug. If can't compile WIN64Debug, try to remove /GZ.
11. It is up to discover and experience more.    
