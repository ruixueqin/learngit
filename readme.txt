import zipfile
import os
import gzip
import csv
#from pathlib import Path



file_list = os.listdir(r'.')
i=0
file_gz=[]
for file_name in file_list:
    if os.path.splitext(file_name)[1] == '.gz':
        print(file_name)
        file_gz.append(file_name)

print(file_gz)
#以上匹配后缀为gz的文件


file_csv=[]
for file_name in file_gz:
    f_name = file_name.replace(".gz", str(i)+".csv ")
    #获取文件的名称，去掉
    i+=1
    g_file = gzip.GzipFile(file_name)
    #创建gzip对象
    open(f_name, "wb+").write(g_file.read())
    #gzip对象用read()打开后，写入open()建立的文件里。
    g_file.close()
    file_csv.append(f_name)
#以上是把匹配的文件解压改名

m=0
for file in file_csv:
    csv_file = open('file', 'r', encoding="utf-8")
    csv_keyword = csv.reader(csv_file)
    #keywords = []
    if m==0:
        n = 0
        m=1
        keywords = []
        for row in csv_keyword:
            keywords.append(row[0].split())
            n += 1
            if n > 1:  # 只查前2两行的数据
                break
        print(keywords)  #
        print(keywords[0][2], keywords[1][0], keywords[1][1])
        csv_file.close()
        counter = keywords[0][2]
        entity = keywords[1][0]
        time = keywords[1][1]
    print(entity,time,counter)
    eles:
        keywords2 = []
        n2 = 0
        for row in csv_keyword:
            keywords2.append(row[0].split())
        # n2 += 1
        # if n2 > 1:  # 只查前2两行的数据
        #    break
        # print(keywords)  #
        # print(keywords[0][2],keywords[1][0],keywords[1][1])
            if entity in row:
            print(row[0], row[1], row[2])
            break  # 最后一个不要这个
    # print(keywords2)
    csv_file2.close()
    # print(keywords[0][2])

    print(keywords)  #
    print(keywords[0][2], keywords[1][0], keywords[1][1])
    csv_file.close()
    zhibiao = keywords[0][2]
    entity = keywords[1][0]
    time = keywords[1][1]

    csv_file2 = open('test2.csv', 'r', encoding="utf-8")
    csv_keyword2 = csv.reader(csv_file2)

    keywords2 = []
    n2 = 0
    for row in csv_keyword2:
        keywords2.append(row)
        # n2 += 1
        # if n2 > 1:  # 只查前2两行的数据
        #    break
        # print(keywords)  #
        # print(keywords[0][2],keywords[1][0],keywords[1][1])
        if entity in row:
            print(row[0], row[1], row[2])
            break  # 最后一个不要这个
    # print(keywords2)
    csv_file2.close()
    # print(keywords[0][2])
