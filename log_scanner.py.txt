# log_scanner.py

# A simple log scanner that looks for suspicious keywords

suspicious_keywords = ["failed", "unauthorized", "denied", "error", "invalid", "attack"]

def scan_log(file_path):
    try:
        with open(file_path, 'r') as file:
            lines = file.readlines()
            print(f"\n🔍 Scanning {file_path} for suspicious activity...\n")
            for i, line in enumerate(lines):
                for word in suspicious_keywords:
                    if word.lower() in line.lower():
                        print(f"Suspicious log [Line {i+1}]: {line.strip()}")
    except FileNotFoundError:
        print("❌ Log file not found.")
    except Exception as e:
        print(f"⚠️ Error: {e}")

# Sample log file path
log_file = "sample_log.txt"
scan_log(log_file)
