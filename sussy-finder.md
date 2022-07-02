
### CodeIgniter database configuration
```
find . -path config/database.php
```

### Database configuration (generic)
```
find . -name database.php
```

### WordPress config file
```
find . -name wp-config.php
```

### *.sql files
```
find . -name \*.sql -exec du -hs {} \;
```

### *.sql files, sorted by increasing size
```
find . -name "*.sql" -exec du -hs {} \; | sort -h
```

### Amazon RDS configuration
```
grep -C 10 -r rds.amazonaws.com --exclude-dir="*/vendor/*"
```

### .env file
```
find . -name .env
```

### Files containing the word "database"
```
grep -C 10 -r --exclude="*.{js,css,html}" -i database
```

### Call to phpinfo()
```
grep -r -F \
  --include="*.php" \
  --exclude-dir="*{vendor,wp-includes}" \
  --exclude="*.{js,css,html,md,txt}" \
  phpinfo
```

### File uploader
```
grep -r -F \
  --include=\*.php \
  --exclude-dir=\*{vendor,wp-includes,vendor_prefixed} \
  -e move_uploaded_file
  -e \$_FILES
```

```
find . -type f -name "*upload*.php"
```

```
find . -type f -name \*upload\*.php
```

### Find sussy bakas
```
grep -r -F \
  --include="*.php" \
  -e "eval(" \
  -e "eval (" \
  -e "base64_decode("
  -e "base64_decode ("
```

```
grep -r -F \
  --include="*.php" \
  -e "system(" \
  -e "system (" \
  -e "passthru(" \
  -e "passthru (" \
  -e "shell_exec(" \
  -e "shell_exec (" \
  -e "exec(" \
  -e "exec ("
```

### Private keys
```
grep -r -F -i -E "BEGIN (\w+) PRIVATE KEY" \
  --exclude-dir="*/vendor"
```
