# SSx (Scoop **Super Search**) 

## Original by [okibcn/ss](https://github.com/okibcn/ss)

<br/>

Scoop Super Search, instantaneous results, UTF-8 and regex compatible. The fastest search engine for Scoop.

(Do you like it? give it a ⭐ to [**okibcn/ss**](https://github.com/okibcn/ss) (and also here))

<br/>
<img width="1548" alt="image" src="https://user-images.githubusercontent.com/22417711/221735191-c92cf442-b29e-411b-a5c7-2b3ca8de6d50.png">

____

## **FEATURES**

<br/>

### - 🛸 **'Outta This World' speed**

<br/>

**Scoop Super Search** is capable of searching in more than 800 buckets and 52,000 app manifests in internet. It uses the lightning fast [ScoopMaster database](https://github.com/letscoop/ScoopMaster) to provide intantaneous results in less than 500 ms.

<br/>

### - ⭐ **Always updated**
<br/>

**Scoop Super Search** uses the [ScoopMaster database](https://github.com/letscoop/ScoopMaster), ensuring the latest results and highest versions for every app in Scoop. The database is updated every 30 minutes, ensuring fresh results, newer than even the official scoop app database.

<br/>

### - 🔍 **Searches in names AND descriptions improving the search flexibility.**
<br/>

Most Scoop search tools provide results only referred to the app name. SSx can search also in the app descriptions.

<br/>

### - 🔍&🔍 **Match All keywords capability.** 
<br/>

Most Scoop search systems provide results for a single keyword. SSx can search combinations of OR and AND.

<br/>

### - 🔧 **Complex REGEX search patterns for advanced users**
<br/>

**SSx** also supports extended **REGEX** pattern seaches, accepting even multiple regex patterns.

<br/>

### - **(音乐) UTF-8 compatible**
<br/>

**SSx** accepts searches in UTF-8 encoding, supporting searches in descriptions when the language uses suplemental Unicode pages. Please note that this feature requires a UTF-8 capable terminal such as Windows Terminal.

<br/>

### - 🕒 **Last-manifest filter**
<br/>

Typical search utilities provide only the list of matches including all the versions and all the manifests for that app. **SSx** can also filter out all the noise in the report, displaying only the latests manifest of the highest version of each app.

<br/>

### - 🎨 **Color coding for quick reference**
<br/>

The result is displated with color coding for easy identigication of the matched words, the official buckets, and the bucket of the newer manifest available for each app.

<br/>

### - 🪟 **Interoperability with other PowerShell scripts**
<br/>

**SSx** can provide the output as a PSObject format so other PowerShell utilities could use the data for other tasks.

<br/>

### - 🌐 **Homepage information**
<br/>

**SSx** has an option that displays the homepage of each manifest. That makes easier to reasearch the source of the app, find details about it, etc.

<br/>

### - 🌐 **Backward compatible with Windows PowerShell 5.1**
<br/>

**SSx** Is compatible with the powerfull and fast Powershell Core from MS Store, or with the default Windows Powrshell included with Windows 10/11.

<br/>


____

<br/>

## **INSTALLATION**
<br/>

This app is a CLI utility for the Scoop framework and requires [Scoop ackage Manager](http://scoop.sh) as a pre-requisite.

From there the installation is straightforward.

1. Add the Let's Scoop meta-bucket:
```pwsh
scoop bucket add .LS http://github.com/thecats1105/letscoop
```
2. Install **SSx**:
```pwsh
scoop install ssx
```

App update:
```pwsh
scoop update ssx
```

App uninstall:
```pwsh
scoop uninstall ssx
```

<br/>

____

<br/>

## **USAGE**

<br/>

Usage: ss [ [ [-n] [ -s|-e ] [-l] [-o] [-p] [-r] ] | -h ] [Search_Patterns]

 **SSx** searches in all the known buckets at a lighning speed. It not only searches
 in the name field, but also in the desscription. Regex and UTF-8 compatible. 
 
 If you use more than one pattern, **SSx** returns manifests matching all of them.
```
 Options:

  no opt. searches for all the matches in the name and description fields.
     -n   Searches only in the name field.
     -s   Simple search. searches an exact name match (implies -n).
     -e   Full expanded regex search.
     -l   Search latest versions only.
     -o   Search only in official buckets.
     -p   Shows homepage for each manifest.
     -r   raw, no color and no header. Outputs data as a PowerShell object.
     -h   Shows this help.
```

<br/>

____

<br/>

## **EXAMPLES**

<br/>

- Search for all the packages with both words in the name or description:
```pwsh
ss scoop search
```
- Search for an app in which the name contains both 'nvidia' AND 'driver'
```pwsh
ss -n nvidia driver 
```
- Simple search for the **ss** app
```pwsh
ss -s ss 
```
- Returns apps containing 'tool' and, 'nvidia' or 'radeon'
```pwsh
ss -n "nvidia|radeon" tool
```
- Get the latest manifests of scoop search utilities
```pwsh
ss -l search scoop 
```
- latests versions of apps ending in 'ss' starting with 's'
```pwsh
ss -n -l -e ss$ ^s 
```
- UTF-8 search of all the apps containing the word 音乐 (music) in the description.
```pwsh
ss -l 音乐 
```
- stores in the `$apps` variable a PSObject with all the Scoop manifests — more than 52,000.
```pwsh
$apps = ss -r .* 
```
