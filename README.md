




import java.util.Scanner;

public class Main {

	public static void F(int col, int row, int colr, int rowr, char prec,
			char color, char[][] matrix) {

		if(col-1>=0&&(matrix[col-1][row]==prec)&&matrix[col-1][row]!=color){
			
			matrix[col-1][row]=color;
			F(col-1,row,colr,rowr,prec,color,matrix);
		}
		 if(col+1<=colr&&(matrix[col+1][row]==prec)&&matrix[col+1][row]!=color){
			 
			matrix[col+1][row]=color;
			F(col+1,row,colr,rowr,prec,color,matrix);
		}
		 if(row-1>=0&&(matrix[col][row-1]==prec)&&matrix[col][row-1]!=color){
			 
			matrix[col][row-1]=color;
			F(col,row-1,colr,rowr,prec,color,matrix);
		}
		 if(row+1<=rowr&&(matrix[col][row+1]==prec)&&matrix[col][row+1]!=color){
			 
			matrix[col][row+1]=color;
			F(col,row+1,colr,rowr,prec,color,matrix);
		}
	}

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);

		char matrix[][] = new char[0][0];

		int first = 0;
		int second = 0;
		while (sc.hasNext()) {

			char print = sc.next().charAt(0);

			if (print == 'I') {

				first = sc.nextInt();
				second = sc.nextInt();
				
				matrix = new char[second][first];
				for (int i = 0; i < second; i++) {
					for (int j = 0; j < first; j++) {

						matrix[i][j] = 'O';
					}
				}
			} else if (print == 'C') {

				for (int i = 0; i < second; i++) {
					for (int j = 0; j < first; j++) {

						matrix[i][j] = 'O';
					}
				}
			} else if (print == 'L') {

				int f = sc.nextInt();
				int s = sc.nextInt();
				char color = sc.next().charAt(0);
				if (f > 1 && s > 1) {
					f--;
					s--;
				} else if (f > 1) {
					f--;
				} else if (s > 1) {
					s--;
				}
				matrix[s][f] = color;
			}

			else if (print == 'V') {
				int row = sc.nextInt();
				int col1 = sc.nextInt();
				int col2 = sc.nextInt();
				char color = sc.next().charAt(0);

				if (col1 > col2) {
					int temp = col1;
					col1 = col2;
					col2 = temp;
				}
				if (row >= 1) {
					row--;
				}
				if (col1 >= 1) {
					col1--;
				}

				for (int i = col1; i < col2; i++) {
					matrix[i][row] = color;
				}
			} else if (print == 'H') {
				int row1 = sc.nextInt();
				int row2 = sc.nextInt();
				int col = sc.nextInt();
				char color = sc.next().charAt(0);
				if (row1 > row2) {
					int temp = row1;
					row1 = row2;
					row2 = temp;
				}
				if (col >= 1) {
					col--;
				}
				if (row1 >= 1) {
					row1--;
				}

				for (int i = row1; i < row2; i++) {
					matrix[col][i] = color;
				}
			} else if (print == 'K') {
				int col1 = sc.nextInt();
				int row1 = sc.nextInt();
				int col2 = sc.nextInt();
				int row2 = sc.nextInt();
				char color = sc.next().charAt(0);

				if (col1 > col2) {
					int temp = col1;
					col1 = col2;
					col2 = temp;
				}
				if (row1 > row2) {
					int temp = row1;
					row1 = row2;
					row2 = temp;
				}
				if (col1 >= 1) {
					col1--;
				}
				if (row1 >= 1) {
					row1--;
				}

				for (int i = col1; i < col2; i++) {
					for (int j = row1; j < row2; j++) {
						matrix[i][j] = color;
					}
				}
			} else if (print == 'S') {

				String count = sc.next();

				System.out.println(count);

				for (int i = 0; i < second; i++) {
					for (int j = 0; j < first; j++) {

						System.out.print(matrix[i][j]);
					}
					System.out.println();
				}
			} else if (print == 'F') {

				int col = sc.nextInt();
				int row = sc.nextInt();
				char color = sc.next().charAt(0);
				int colr = second - 1;
				int rowr = first - 1;
				char prec = matrix[col - 1][row - 1];
				Main.F(col, row, colr, rowr, prec, color, matrix);

			} else if (print == 'X') {
				break;
			}

		}

		sc.close();
	}
}
